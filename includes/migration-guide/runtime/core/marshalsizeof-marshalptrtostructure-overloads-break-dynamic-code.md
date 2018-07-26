### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Marshal.SizeOf a přetížení Marshal.PtrToStructure přerušit dynamický kód

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5.1, dynamické vazby na metody <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, nebo <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (prostřednictvím Windows Powershellu, IronPython nebo dynamické klíčové slovo C#, například) může mít za následek <code>MethodInvocationExceptions</code> vzhledem k tomu, že byly přidány nové přetížení z těchto metod, které můžou být nejednoznačná skriptovacích strojů.|
|Návrh|Aktualizujte skripty, které jasně označují, které přetížení by mělo být použito. To může, obvykle provádí přetypováním explicitní parametry typu metody jako <xref:System.Type>. Zobrazit [tento odkaz](https://support.microsoft.com/kb/2909958/) další podrobnosti a příklady, jak chcete-li vyřešit tento problém.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Modul runtime|

