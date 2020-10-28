<template>
     <img 
     draggable="false"
    src="../assets/map3.jpg" 
    class="map">
</template>

<script>
   import $ from 'jquery/src/jquery';
   import pep from '../../bower_components/pep/src/jquery.pep';

   export default{
       created: onCreate
    }
    function boundaryCalculator(map,viewreport){
        const top = viewreport.height()-map.height();
        const left = viewreport.width()-map.width();
        return [top, 0, 0, left];
    }
    function onCreate(){
        $(document).ready( ()=>{
            const $map = $('.map');
            const $viewreport = $('window');
            const constrainTo = boundaryCalculator($map,$viewreport);


            $map.on('load',()=>{
                $map.pep({ constrainTo});
            })
        });
    }
</script>

<style>
.map{
    cursor: move;
    perspective: 1000px;
    backface-visibility: hidden;
    /* width: 100%;
    height: 100%; */
}
</style>