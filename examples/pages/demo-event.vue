<template>
    <div class="demo-event">
        <demo-block :code="code">
            <template slot="preview">
                <model-obj :backgroundAlpha="0"
                    @on-mousemove="onMouseMove"
                    src="static/models/obj/LeePerrySmith.obj"></model-obj>
            </template>
        </demo-block>
    </div>
</template>

<script>
import DemoBlock from '../components/demo-block';
import hljs from 'highlight.js'
import ModelObj from '../../src/model-obj.vue'

const code = `

<template>
    <model-obj src="static/models/obj/LeePerrySmith.obj"></model-obj>
</template>

<script>
    import { ModelObj } from 'vue-3d-model'

    export default {
        components: {
            ModelObj
        }
    }
<\/script>

`

export default {
    name: 'demo-event',
    data () {
    	return {
            code,
    		intersected: null
    	}
    },
    methods: {
        onMouseMove ( intersected ) {
            if ( intersected ) {
                intersected.object.material.color.setHex( 0xff0000 )
            }
            console.log( intersected )
        }
    },
    components: {
        ModelObj,
        DemoBlock
    }
}
</script>
<style>
	.demo-event {
        padding: 20px;
        background: #fff;
        box-shadow: 0 2px 4px 0 rgba(0,0,0,.1), 0 16px 24px 0 rgba(81,129,228,.1);
	}
</style>
