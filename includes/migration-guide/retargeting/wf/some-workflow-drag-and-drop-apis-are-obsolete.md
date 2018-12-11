### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>Některá rozhraní API a přetahování pracovního postupu jsou popsané zastaralé

|   |   |
|---|---|
|Podrobnosti|Toto rozhraní API a přetažení pracovní postup je zastaralá a způsobí upozornění kompilátoru, že pokud aplikace je znovu sestavit na 4.5.|
|Doporučení|Nové <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> by místo toho použít rozhraní API, které podporují operace s více objekty. Alternativně lze potlačit upozornění sestavení nebo lze se vyhnout pomocí staršího kompilátoru. Rozhraní API jsou stále podporovány.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|

