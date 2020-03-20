---
title: Tlbexp.exe (exportér knihovny typů)
ms.date: 03/30/2017
helpviewer_keywords:
- exporting type library [.NET Framework]
- exporter tool [.NET Framework]
- Tlbexp.exe
- Type Library Exporter
- type libraries [.NET Framework], exporting
ms.assetid: a487d61b-d166-467b-a7ca-d8b52fbff42d
ms.openlocfilehash: 1d2380ff607836b5dc15e7194b90dd3a53d1d2c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180275"
---
# <a name="tlbexpexe-type-library-exporter"></a>Tlbexp.exe (exportér knihovny typů)
Exportér knihovny typů generuje knihovny typů, které popisují typy definované v sestavení Common Language Runtime.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
tlbexp assemblyName [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*Assemblyname*|Sestavení, pro které se má exportovat knihovna typů.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/asmpath:** *adresář*|Určuje umístění, ve kterém se mají hledat sestavení. Pokud použijete tuto možnost, musíte explicitně zadat umístění, ve kterém se mají hledat odkazovaná sestavení, včetně aktuálního adresáře.<br /><br /> Při použití **možnosti asmpath** exportér knihovny typů nebude hledat sestavení v globální mezipaměti sestavení (GAC).|  
|**/nápověda**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/names:** *název souboru*|Určuje velikost písmen názvů v knihovně typů. Argument *název souboru* je textový soubor. Každý řádek v souboru určuje velikost písmen jednoho názvu v knihovně typů.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/oldnames**|Donutí Tlbexp.exe exportovat upravené názvy typů, jestliže dojde ke konfliktu názvu typů. Toto bylo výchozí chování ve verzích rozhraní .NET Framework nižších než 2.0.|  
|**/out:** *soubor*|Určuje název souboru knihovny typů, který má být vytvořen. Pokud tento parametr vynecháte, Tlbexp.exe vygeneruje knihovnu typů se stejným názvem, jako je název sestavení (skutečný název sestavení, který nemusí být nutně stejný jako název souboru obsahujícího sestavení), a s příponou .tlb.|  
|**/ticho:**`warningnumber`|Potlačí zobrazení konkrétního upozornění. Tuto možnost nelze použít s **parametrem /silent**.|  
|**/silent**|Potlačí zobrazování zpráv o úspěšném dokončení. Tuto možnost nelze použít s **parametrem /silence**.|  
|**/tlbreference:** *název knihovny typu*|Donutí Tlbexp.exe explicitně vyřešit odkazy typu knihovny bez konzultace s registrem. Například, pokud sestavení B odkazuje na sestavení A, můžete použít tuto možnost k poskytnutí explicitního odkazu na knihovnu typů a nespoléhat se na knihovnu typů zadanou v registru. Tlbexp.exe provádí kontroly verze pro zajištění, že verze knihovny typů bude odpovídat verzi sestavení; pokud verze knihovny neodpovídá, dojde k chybě.<br /><br /> Všimněte si, že možnost **tlbreference** stále <xref:System.Runtime.InteropServices.ComImportAttribute> konzultuje v registru v případech, kdy je atribut použit na rozhraní, které je pak implementováno jiným typem.|  
|**/tlbrefpath:** *cesta*|Plně kvalifikovaná cesta na odkazovanou knihovnu typů.|  
|**/win32**|Při kompilaci na 64bitovém počítači tato možnost určuje, že Tlbexp.exe vygeneruje 32bitovou knihovnu typů.|  
|**/win64**|Při kompilaci na 32bitovém počítači tato možnost určuje, že Tlbexp.exe vygeneruje 64bitovou knihovnu typů.|  
|**/podrobné informace**|Určuje režim podrobného vypisování; zobrazí seznam všech odkazovaných sestavení, pro která je třeba vytvořit knihovnu typů.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
> [!NOTE]
> Možnosti příkazového řádku pro Tlbexp.exe nerozlišují malá a velká písmena a lze je zadat v libovolném pořadí. Pro jednoznačnou identifikaci je potřeba pouze poskytnout dostatek parametrů. Například **/n** je ekvivalentní **/nologo**a **/o:** *outfile.tlb* je ekvivalentní **/out:** *outfile.tlb*.  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Tlbexp.exe vygeneruje knihovnu typů obsahující definice typů definovaných v sestavení. Aplikace jako například Visual Basic 6.0 může použít vygenerovanou knihovnu typů ke svázání s typy rozhraní .NET definovanými v sestavení.  
  
> [!IMPORTANT]
> Pomocí nástroje Tlbexp.exe nelze exportovat soubory metadat systému Windows (.winmd). Export sestavení modulů Windows Runtime není podporován.  
  
 Celé sestavení se převede najednou. Pomocí nástroje Tlbexp.exe nelze generovat informace o typu pro podtypy definované v sestavení.  
  
 Pomocí příkazu Tlbexp.exe nelze vytvořit knihovnu typů ze sestavy, která byla importována pomocí [importu knihovny typů (Tlbimp.exe).](tlbimp-exe-type-library-importer.md) Místo toho byste měli použít původní knihovnu typů, která byla importována pomocí nástroje Tlbimp.exe. Knihovny typů můžete exportovat ze sestavení, která odkazují na sestavení, jež byla importována pomocí nástroje Tlbimp.exe. Příklady najdete v části níže.  
  
 Nástroj Tlbexp.exe umístí vytvořenou knihovnu typů do aktuálního pracovního adresáře nebo do adresáře určeného pro výstupní soubor. Jediné sestavení může způsobit vygenerování několika knihoven typů.  
  
 Nástroj Tlbexp.exe vygeneruje knihovnu typů, ale nezaregistruje ji. To je na rozdíl od [nástroje registrace sestavení (Regasm.exe)](regasm-exe-assembly-registration-tool.md), který generuje a registruje knihovnu typů. Chcete-li vygenerovat a zaregistrovat knihovnu typů s modelem COM, použijte nástroj Regasm.exe.  
  
 Pokud nezadáte možnost `/win32` nebo, `/win64` program Tlbexp.exe vygeneruje 32bitovou nebo 64bitovou knihovnu typů, která odpovídá typu počítače, ve kterém provádíte kompilaci (32bitový nebo 64bitový počítač). Pro účely křížové kompilace můžete `/win64` tuto možnost použít v 32bitovém počítači ke generování `/win32` knihovny 64bitového typu a tuto možnost můžete použít v 64bitovém počítači ke generování knihovny 32bitového typu. V knihovnách 32bitových <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> typů je <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>hodnota nastavena na hodnotu . V 64bitových knihovnách <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> typů je <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>hodnota nastavena na hodnotu . Všechny transformace datového typu (například datové typy `IntPtr` velikosti ukazatele, například a `UIntPtr`) jsou převedeny odpovídajícím způsobem.  
  
 Pokud použijete <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut k <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> určení `VT_UNKOWN` `VT_DISPATCH`hodnoty nebo , tlbexp.exe ignoruje <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> jakékoli následné použití pole. Například při následujících podpisech:  
  
```csharp
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_UNKNOWN, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructUnkSafe(){return null;}  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_DISPATCH, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructDispSafe(){return null;}  
```  
  
 je vygenerována následující knihovna typů:  
  
```cpp
[id(0x60020004)]  
HRESULT StructUnkSafe([out, retval] SAFEARRAY(IUnknown*)* pRetVal);  
[id(0x60020005)]  
HRESULT StructDispSafe([out, retval] SAFEARRAY(IDispatch*)* pRetVal);  
```  
  
 Všimněte si, že tlbexp.exe ignoruje <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> pole.  
  
 Vzhledem k tomu, že knihovny typů nemohou pojmout všechny informace, které jsou součástí sestavení, nástroj Tlbexp.exe může zrušit některá data během exportu. Vysvětlení transformačního procesu a identifikaci zdroje každé informace vysílané do knihovny typů naleznete v [souhrnu převodu knihovny typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))sestavení .  
  
 Všimněte si, že exportér knihovny typů exportuje metody, které mají <xref:System.TypedReference> parametry jako `VARIANT`, i když <xref:System.TypedReference> objekt nemá žádný význam v nespravovaném kódu. Při exportu metod, které mají <xref:System.TypedReference> parametry, exportér knihovny typů nevygeneruje upozornění nebo chybu a nespravovaný kód, který používá výslednou knihovnu typů, nebude pracovat správně.  
  
 Exportér knihovny typů je podporován v systému Microsoft Windows 2000 a novějším.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz generuje knihovnu typů se stejným názvem `myTest.dll`jako sestavení nalezené v .  
  
```console  
tlbexp myTest.dll  
```  
  
 Následující příkaz generuje knihovnu typů `clipper.tlb`s názvem .  
  
```console  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 Následující příklad ukazuje použití nástroje Tlbexp.exe k exportování knihovny typů ze sestavení, které odkazuje na sestavení, jež byla importována pomocí nástroje Tlbimp.exe.  
  
 Nejprve použijte tlbimp.exe k `myLib.tlb` importu `myLib.dll`knihovny typů a uložte ji jako .  
  
```console  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 Následující příkaz používá kompilátor Jazyka `Sample.dll,` C# `myLib.dll` ke kompilaci odkazů vytvořených v předchozím příkladu.  
  
```console  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 Následující příkaz generuje knihovnu `Sample.dll` typů pro `myLib.dll`tyto odkazy .  
  
```console  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.TypeLibExporterFlags>
- [Nástroje](index.md)
- [Regasm.exe (nástroj registrace sestavení)](regasm-exe-assembly-registration-tool.md)
- [Souhrn převodu knihovny sestavení k typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))
- [Tlbimp.exe (importér knihovny typů)](tlbimp-exe-type-library-importer.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
