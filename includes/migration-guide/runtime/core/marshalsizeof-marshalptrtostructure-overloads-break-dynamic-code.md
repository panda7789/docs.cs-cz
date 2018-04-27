### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Marshal.SizeOf a Marshal.PtrToStructure přetížení rozdělit dynamický kód

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5.1, dynamické vazby metody <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, nebo <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (pomocí prostředí Windows PowerShell, IronPython nebo C# dynamické klíčové slovo, např.) může mít za následek <code>MethodInvocationExceptions</code> vzhledem k tomu, že byly přidány nové přetížení těchto metod, které mohou být nejednoznačný k skriptovacích strojů.|
|Návrh|Aktualizace skriptů jasně znamenat přetížení, které je třeba použít. To může obvykle provádí explicitně přetypování parametry typu tyto metody jako <xref:System.Type>. V tématu [tento odkaz](https://support.microsoft.com/kb/2909958/) další podrobnosti a příklady, jak vyřešit problém.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Modul runtime|

