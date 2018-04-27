### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>Rozhraní API pro přetažení myší některé pracovního postupu jsou popsané zastaralé

|   |   |
|---|---|
|Podrobnosti|Toto rozhraní API a přetažení pracovního postupu je zastaralá a způsobí upozornění kompilátoru, pokud aplikace je znovu sestaven proti 4.5.|
|Návrh|Nové <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> by měl být místo toho použít rozhraní API, které podporují operace s více objektů. Alternativně lze potlačit upozornění sestavení nebo se můžete vyhnout pomocí starší kompilátoru. Rozhraní API jsou stále podporovány.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|

