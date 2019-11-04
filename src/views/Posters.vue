<template>
  <div class="posters">
    <h1>Configure a poster</h1>
    <!-- {{propertyGroups}} -->
	<div v-for="propertyGroup in postersJson.propertyGroups" v-if="propertyGroup.inSelector && propertyGroup.title.nl === 'Formaat'">
      <h3>{{ propertyGroup.title.nl }}</h3>
      <div>
        <strong>Kies je {{propertyGroup.properties[0].title.nl}}</strong>
        <div class="step1">
          <div class="property-selector">
				  <div class="select-tab" @click="step1ActiveTab = 'a_formaten'">A-Formaten</div>
				  <div class="select-tab"  @click="step1ActiveTab = 'b_formaten'">B-Formaten</div>
				  <div class="select-tab"  @click="step1ActiveTab = 'pavement_sign'">Stoepbord posters</div>
				  <div class="select-tab"  @click="step1ActiveTab = 'specials'">Specials</div>
          </div>

		  <div class="properties">
			  <div class="a-formaten" v-if="step1ActiveTab === 'a_formaten'">
				<ul v-for="option in propertyGroup.properties[0].options">
					<li v-if="option.parent === 'a_formaten'">
						<input
						type="radio"
						:value="option.name && option.name.nl"
						:id="option.slug"
						:name="propertyGroup.properties[0].title.nl"
						/>
						<label :for="option.slug">{{ option.name && option.name.nl }}</label>
					</li>
				</ul>
			  </div>
			  <div class="b-formaten" v-if="step1ActiveTab === 'b_formaten'">
				  <ul v-for="option in propertyGroup.properties[0].options">
					<li v-if="option.parent === 'b_formaten'">
					<input
						type="radio"
						:value="option.name && option.name.nl"
						:id="option.slug"
						:name="propertyGroup.properties[0].title.nl"
					/>
					<label :for="option.slug">{{ option.name && option.name.nl }}</label>
					</li>
				  </ul>
			  </div>
			  <div class="pavement-sign" v-if="step1ActiveTab === 'pavement_sign'">
				<ul v-for="option in propertyGroup.properties[0].options">
					<li v-if="option.parent === 'pavement_sign'">
						<input
						type="radio"
						:value="option.name && option.name.nl"
						:id="option.slug"
						:name="propertyGroup.properties[0].title.nl"
						/>
						<label :for="option.slug">{{ option.name && option.name.nl }}</label>
					</li>
				</ul>
			  </div>
			  <div class="specials" v-if="step1ActiveTab === 'specials'">
				<ul v-for="option in propertyGroup.properties[0].options">
					<li v-if="option.parent === 'specials'">
						<input
						type="radio"
						:value="option.name && option.name.nl"
						:id="option.slug"
						:name="propertyGroup.properties[0].title.nl"
						/>
						<label :for="option.slug">{{ option.name && option.name.nl }}</label>
					</li>
				</ul>
			  </div>
		  </div>
        </div>

		<strong>Kies je {{propertyGroup.properties[1].title.nl}}</strong>
		<div class="step2">
          <div class="property-selector">
				  <div class="select-tab"  @click="step2ActiveTab = 'pms'">PMS</div>
				  <div class="select-tab"  @click="step2ActiveTab = 'full_color'">Full color</div>
				  <div class="select-tab"  @click="step2ActiveTab = 'full_color_backside_abri'">Full color backside abri</div>
          </div>

		  <div class="properties">
			  <div class="pms" v-if="step2ActiveTab === 'pms'">
				<ul v-for="option in propertyGroup.properties[1].options">
					<li v-if="option.parent === 'pms'">
						<input
						type="radio"
						:value="option.name && option.name.nl"
						:id="option.slug"
						:name="propertyGroup.properties[1].title.nl"
						/>
						<label :for="option.slug">{{ option.name && option.name.nl }}</label>
					</li>
				</ul>
			  </div>
			  <div class="full_color" v-if="step2ActiveTab === 'full_color'">
				  <ul v-for="option in propertyGroup.properties[1].options">
					<li v-if="option.parent === 'full_color'">
					<input
						type="radio"
						:value="option.name && option.name.nl"
						:id="option.slug"
						:name="propertyGroup.properties[1].title.nl"
					/>
					<label :for="option.slug">{{ option.name && option.name.nl }}</label>
					</li>
				  </ul>
			  </div>
			  <div class="full_color_backside_abri" v-if="step2ActiveTab === 'full_color_backside_abri'">
				<ul v-for="option in propertyGroup.properties[1].options">
					<li v-if="option.parent === 'full_color_backside_abri'">
						<input
						type="radio"
						:value="option.name && option.name.nl"
						:id="option.slug"
						:name="propertyGroup.properties[1].title.nl"
						/>
						<label :for="option.slug">{{ option.name && option.name.nl }}</label>
					</li>
				</ul>
			  </div>
		  </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import json from "../json/posters.json";

export default {
  data() {
    return {
	  postersJson: json,
	  step1ActiveTab: 'a_formaten',
	  step2ActiveTab: 'pms'
    };
  },
  computed: {
	propertyGroups() {
		return json.propertyGroups.map((item) => {
			return item.title.nl
		})
	}
  }
};
</script>

<style lang="scss">
.posters {
  max-width: 960px;
  margin: 0 auto;
  text-align: left;

  .property-selector {
	   .select-tab {
		   cursor: pointer;
		   text-decoration: underline;
	   }
  }

	.step1, .step2 {
		display: flex;

		> * {
			display: inline-block;
			width: 50%;
		}
		.properties {
			ul {
				padding: 0;
				list-style-type: none;

				li {
					input {
						margin-right: 12px;
					}
				}
			}
		}
	}

  
}
</style>
