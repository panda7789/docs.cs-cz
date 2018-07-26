### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>PreviewLostKeyboardFocus je voláno opakovaně její obslužná rutina se zobrazí okno se zprávou Windows Forms

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5, volání <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> z <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> způsobí, že obslužná rutina obslužnou rutinu znovu vyvolána při zavření okna se zprávou, může mít za následek nekonečnou smyčku okna se zprávou.|
|Návrh|Chcete-li tento problém obejít dvěma způsoby:<ol><li>Může se jim vyhnout voláním <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> místo <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</li><li>Může se jim vyhnout tím, že zobrazuje zprávy <xref:System.Windows.UIElement.LostKeyboardFocus?displayProperty=nameWithType> obslužné rutiny události (nikoli <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=name> obslužná rutina události).</li></ol>|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|

