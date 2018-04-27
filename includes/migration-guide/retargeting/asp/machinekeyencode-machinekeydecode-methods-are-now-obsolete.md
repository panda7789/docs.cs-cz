### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>Metody MachineKey.Encode a MachineKey.Decode jsou nyní zastaralé

|   |   |
|---|---|
|Podrobnosti|Tyto metody jsou nyní zastaralé. Kompilace kódu volající tyto metody vede k upozornění překladače.|
|Návrh|Jsou doporučených alternativách <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> a <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>. Alternativně lze potlačit upozornění sestavení, nebo se můžete vyhnout pomocí starší kompilátoru. Rozhraní API jsou stále podporovány.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|

