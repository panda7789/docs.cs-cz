### <a name="encoderparameter-ctor-is-obsolete"></a>Konstruktoru EncoderParameter je zastaralá

|   |   |
|---|---|
|Podrobnosti|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> Konstruktor je nyní zastaralý a zavádí sestavení upozornění, pokud se používá.|
|Návrh|I když <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>konstruktor budou nadále fungovat, následující konstruktor musí být použit místo abyste se vyhnuli upozornění na zastaralé sestavení při znovu kompilování kódu nástroje pro rozhraní .NET Framework 4.5: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

