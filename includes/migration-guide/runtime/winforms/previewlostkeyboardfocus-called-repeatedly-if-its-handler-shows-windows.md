### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>PreviewLostKeyboardFocus je volána opakovaně, pokud jeho obslužná rutina zobrazí okno se zprávou Windows Forms

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, volání <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> z <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> způsobí, že obslužné rutiny obslužná rutina znovu provést při zavření okna se zprávou, může mít za následek nekonečné smyčce oken zpráv.|
|Návrh|Chcete-li vyřešit tento problém dvěma způsoby:<ol><li>Může se vyhnout voláním <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> místo <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</li><li>Může se vyhnout zobrazením poli zprávy <xref:System.Windows.UIElement.LostKeyboardFocus?displayProperty=nameWithType> obslužné rutiny události (Naproti tomu <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=name> obslužné rutiny události).</li></ol>|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|

