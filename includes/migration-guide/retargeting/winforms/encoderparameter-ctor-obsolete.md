### <a name="encoderparameter-ctor-is-obsolete"></a>EncoderParameter ctor je zastaralý.

|   |   |
|---|---|
|Podrobnosti|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> Konstruktor je nyní zastaralé a budou zavedeny upozornění sestavení, pokud se používá.|
|Návrh|I když <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>konstruktoru bude pokračovat v práci, následující konstruktor by měl místo toho použít při opětovné kompilaci kódu pomocí nástroje rozhraní .NET Framework 4.5, aby upozornění zastaralé sestavení: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Mění se cílení|
|Ovlivněné rozhraní API|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

