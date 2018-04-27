### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load neodstraní vlastnost symbol

|   |   |
|---|---|
|Podrobnosti|Při cílení na rozhraní .NET Framework 4.5 v Návrháři pracovních postupů a načítání znovu hostované 3.5 pracovního postupu se <xref:System.Activities.Presentation.WorkflowDesigner.Load> metody <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> je vyvolána při ukládání pracovního postupu.|
|Návrh|Tato chyba manifesty jenom při cílení na rozhraní .NET Framework 4.5 v Návrháři pracovních postupů, takže je možné pracovat kolem nastavením <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> na 4.0 .NET Framework.Alternatively, se můžete vyhnout problém pomocí <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metoda pro načtení pracovního postupu, místo <xref:System.Activities.Presentation.WorkflowDesigner.Load>.|
|Rozsah|Hlavní|
|Version|4.5|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|

