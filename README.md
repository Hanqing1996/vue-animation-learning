#### enter
* v-enter：在元素被插入之前（v-if由false变为true时）生效，在元素被插入之后的下一帧移除。
    * v-enter 的存在时长极短，因为"v-if由false变为true"和"元素被插入"相隔时间极短
* v-enter-active：在元素被插入之前生效（v-if由false变为true时），在过渡/动画完成之后移除。
    * v-enter-active 的存在时长为约过渡时长
* v-enter-to: 在元素被插入之后下一帧生效 (与此同时 v-enter 被移除)，在过渡/动画完成之后移除。
    * v-enter-to 的存在时长约为过渡时长
    * 一般不用v-enter-to
> 稍微总结下（不用记）：v-enter 和 v-enter-active 是同时添加的。v-enter-active 和 v-enter-to 是同时撤销的。

#### key的作用
```
<transition>
  <button v-if="isEditing" key="save">
    Save
  </button>
  <button v-else key="edit">
    Edit
  </button>
</transition>
```
> When toggling between elements that have the same tag name, you must tell Vue that they are distinct elements by giving them unique key attributes. Otherwise, Vue’s compiler will only replace the content of the element for efficiency. Even when technically unnecessary though, it’s considered good practice to always key multiple items within a <transition> component.