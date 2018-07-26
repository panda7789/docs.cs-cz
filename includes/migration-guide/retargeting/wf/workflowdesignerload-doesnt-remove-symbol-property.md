### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load neodebere vlastnost symbol

|   |   |
|---|---|
|Podrobnosti|Při cílení na rozhraní .NET Framework 4.5 v Návrháři pracovních postupů a načítání 3.5 a znovu hostovaných pracovních postupů s <xref:System.Activities.Presentation.WorkflowDesigner.Load> metody <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> je vyvolána při ukládání pracovního postupu.|
|Návrh|Tato chyba projevuje pouze při cílení na rozhraní .NET Framework 4.5 v Návrháři pracovních postupů, takže je možné pracovat kolem tak, že nastavíte <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> na 4.0 .NET Framework.Alternatively může být problém vyhnout použitím <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metodu načtení pracovního postupu, místo <xref:System.Activities.Presentation.WorkflowDesigner.Load>.|
|Rozsah|Hlavní|
|Version|4.5|
|Typ|Mění se cílení|
|Ovlivněné rozhraní API|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|

