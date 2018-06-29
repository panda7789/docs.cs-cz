### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>Pracovní postup vyvolá teď původní výjimka místo výjimky NullReferenceException v některých případech

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 a starší verze, když metoda Execute aktivity pracovního postupu výjimku s <code>null</code> hodnota <xref:System.Exception.Message> způsobí výjimku modulu runtime pracovního postupu systém. vlastnost, <xref:System.NullReferenceException?displayProperty=name>, maskování původní výjimka. V 4.7 rozhraní .NET Framework je vyvolána dříve maskované výjimka.|
|Návrh|Pokud váš kód závisí na zpracování <xref:System.NullReferenceException?displayProperty=name>, změňte ho na catch výjimky, které může být vyvolána z vlastních aktivit.|
|Rozsah|Vedlejší|
|Version|4.7|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|

