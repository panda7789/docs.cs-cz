---
title: Tlbexp.exe (exportér knihovny typů)
description: Zkontrolujte Tlbexp.exe a Exportér knihovny typů. Tento nástroj generuje knihovnu typů, která popisuje typy definované v sestavení modulu CLR (Common Language Runtime).
ms.date: 03/30/2017
helpviewer_keywords:
- exporting type library [.NET Framework]
- exporter tool [.NET Framework]
- Tlbexp.exe
- Type Library Exporter
- type libraries [.NET Framework], exporting
ms.assetid: a487d61b-d166-467b-a7ca-d8b52fbff42d
ms.openlocfilehash: 3cfaa83590fefe31c437d2ff607fb579aec1da61
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517032"
---
# <a name="tlbexpexe-type-library-exporter"></a>Tlbexp.exe (exportér knihovny typů)
Exportér knihovny typů generuje knihovny typů, které popisují typy definované v sestavení Common Language Runtime.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
tlbexp assemblyName [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Description|  
|--------------|-----------------|  
|*Doplňk*|Sestavení, pro které se má exportovat knihovna typů.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/asmPath:** *adresář*|Určuje umístění, ve kterém se mají hledat sestavení. Pokud použijete tuto možnost, musíte explicitně zadat umístění, ve kterém se mají hledat odkazovaná sestavení, včetně aktuálního adresáře.<br /><br /> Při použití možnosti **asmPath** nebude Exportér knihovny typů Hledat sestavení v globální mezipaměti sestavení (GAC).|  
|**/Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/Names:** *název souboru*|Určuje velikost písmen názvů v knihovně typů. Argument *filename* je textový soubor. Každý řádek v souboru určuje velikost písmen jednoho názvu v knihovně typů.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/oldnames**|Donutí Tlbexp.exe exportovat upravené názvy typů, jestliže dojde ke konfliktu názvu typů. Toto bylo výchozí chování ve verzích rozhraní .NET Framework nižších než 2.0.|  
|**/out:** *soubor*|Určuje název souboru knihovny typů, který má být vytvořen. Pokud tento parametr vynecháte, Tlbexp.exe vygeneruje knihovnu typů se stejným názvem, jako je název sestavení (skutečný název sestavení, který nemusí být nutně stejný jako název souboru obsahujícího sestavení), a s příponou .tlb.|  
|**/Silence:**`warningnumber`|Potlačí zobrazení konkrétního upozornění. Tuto možnost nelze použít s **/Silent**.|  
|**/silent**|Potlačí zobrazování zpráv o úspěšném dokončení. Tuto možnost nelze použít s **/Silence**.|  
|**/tlbreference:** *názevknihovnytypů*|Donutí Tlbexp.exe explicitně vyřešit odkazy typu knihovny bez konzultace s registrem. Například, pokud sestavení B odkazuje na sestavení A, můžete použít tuto možnost k poskytnutí explicitního odkazu na knihovnu typů a nespoléhat se na knihovnu typů zadanou v registru. Tlbexp.exe provádí kontroly verze pro zajištění, že verze knihovny typů bude odpovídat verzi sestavení; pokud verze knihovny neodpovídá, dojde k chybě.<br /><br /> Všimněte si, že možnost **tlbreference** stále používá registr v případech <xref:System.Runtime.InteropServices.ComImportAttribute> , kde je atribut použit na rozhraní, které je následně implementováno jiným typem.|  
|**/tlbrefpath:** *cesta*|Plně kvalifikovaná cesta na odkazovanou knihovnu typů.|  
|**/win32**|Při kompilaci na 64bitovém počítači tato možnost určuje, že Tlbexp.exe vygeneruje 32bitovou knihovnu typů.|  
|**/Win64**|Při kompilaci na 32bitovém počítači tato možnost určuje, že Tlbexp.exe vygeneruje 64bitovou knihovnu typů.|  
|**/verbose**|Určuje režim podrobného vypisování; zobrazí seznam všech odkazovaných sestavení, pro která je třeba vytvořit knihovnu typů.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
> [!NOTE]
> Možnosti příkazového řádku pro Tlbexp.exe nerozlišují malá a velká písmena a lze je zadat v libovolném pořadí. Pro jednoznačnou identifikaci je potřeba pouze poskytnout dostatek parametrů. Například **/n** je ekvivalentem **/nologo**a **/o:** *soubor. tlb* je ekvivalentní k **/out:** *soubor. tlb*.  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Tlbexp.exe vygeneruje knihovnu typů obsahující definice typů definovaných v sestavení. Aplikace jako například Visual Basic 6.0 může použít vygenerovanou knihovnu typů ke svázání s typy rozhraní .NET definovanými v sestavení.  
  
> [!IMPORTANT]
> Pomocí nástroje Tlbexp.exe nelze exportovat soubory metadat systému Windows (.winmd). Export sestavení modulů Windows Runtime není podporován.  
  
 Celé sestavení se převede najednou. Pomocí nástroje Tlbexp.exe nelze generovat informace o typu pro podtypy definované v sestavení.  
  
 Tlbexp.exe nelze použít k vytvoření knihovny typů ze sestavení, které bylo importováno pomocí nástroje pro [Import knihovny typů (Tlbimp.exe)](tlbimp-exe-type-library-importer.md). Místo toho byste měli použít původní knihovnu typů, která byla importována pomocí nástroje Tlbimp.exe. Knihovny typů můžete exportovat ze sestavení, která odkazují na sestavení, jež byla importována pomocí nástroje Tlbimp.exe. Příklady najdete v části níže.  
  
 Nástroj Tlbexp.exe umístí vytvořenou knihovnu typů do aktuálního pracovního adresáře nebo do adresáře určeného pro výstupní soubor. Jediné sestavení může způsobit vygenerování několika knihoven typů.  
  
 Nástroj Tlbexp.exe vygeneruje knihovnu typů, ale nezaregistruje ji. To je na rozdíl od [Nástroje pro registraci sestavení (Regasm.exe)](regasm-exe-assembly-registration-tool.md), který generuje a registruje knihovnu typů. Chcete-li vygenerovat a zaregistrovat knihovnu typů s modelem COM, použijte nástroj Regasm.exe.  
  
 Pokud nezadáte `/win32` ani `/win64` možnost nebo, Tlbexp.exe vygeneruje knihovnu typů 32 nebo 64, která odpovídá typu počítače, na kterém provádíte kompilaci (32-bit 64 nebo 16bitový počítač). Pro účely křížové kompilace můžete použít `/win64` možnost na 32 počítače ke generování knihovny typů 64 a můžete použít `/win32` možnost na počítači 64 pro vy32 generování 16bitové knihovny typů. 32 v 64bitových knihovnách typů <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> je hodnota nastavena na <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32> . 64 v 64bitových knihovnách typů <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> je hodnota nastavena na <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64> . Všechny transformace datových typů (například datové typy velikosti ukazatelů, jako jsou `IntPtr` a `UIntPtr` ), jsou vhodně převedeny.  
  
 Použijete-li <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut k zadání <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> hodnoty `VT_UNKOWN` nebo `VT_DISPATCH` , Tlbexp.exe ignoruje jakékoli následné použití <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> pole. Například při následujících podpisech:  
  
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
  
 Všimněte si, že Tlbexp.exe ignoruje <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> pole.  
  
 Vzhledem k tomu, že knihovny typů nemohou pojmout všechny informace, které jsou součástí sestavení, nástroj Tlbexp.exe může zrušit některá data během exportu. Vysvětlení procesu transformace a identifikace zdroje všech informací emitovaných do knihovny typů naleznete v tématu [Souhrn převodu sestavení na knihovnu typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100)).  
  
 Všimněte si, že Exportér knihovny typů exportuje metody, které mají <xref:System.TypedReference> parametry jako `VARIANT` , a to i v případě, že <xref:System.TypedReference> objekt nemá smysl v nespravovaném kódu. Při exportu metod, které mají <xref:System.TypedReference> parametry, Exportér knihovny typů negeneruje upozornění ani chybu a nespravovaný kód, který používá výslednou knihovnu typů, nebude správně fungovat.  
  
 Exportér knihovny typů je podporován v systému Microsoft Windows 2000 a novějším.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vygeneruje knihovnu typů se stejným názvem, jako má sestavení nalezené v `myTest.dll` .  
  
```console  
tlbexp myTest.dll  
```  
  
 Následující příkaz vygeneruje knihovnu typů s názvem `clipper.tlb` .  
  
```console  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 Následující příklad ukazuje použití nástroje Tlbexp.exe k exportování knihovny typů ze sestavení, které odkazuje na sestavení, jež byla importována pomocí nástroje Tlbimp.exe.  
  
 Nejprve použijte Tlbimp.exe pro import knihovny typů `myLib.tlb` a uložte ji jako `myLib.dll` .  
  
```console  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 Následující příkaz používá kompilátor jazyka C# ke kompilaci odkazů, `Sample.dll,` které `myLib.dll` byly vytvořeny v předchozím příkladu.  
  
```console  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 Následující příkaz vygeneruje knihovnu typů pro `Sample.dll` tyto odkazy `myLib.dll` .  
  
```console  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.TypeLibExporterFlags>
- [Nástroje](index.md)
- [Regasm.exe (nástroj registrace sestavení)](regasm-exe-assembly-registration-tool.md)
- [Souhrn převodu sestavení na knihovnu typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))
- [Tlbimp.exe (importér knihovny typů)](tlbimp-exe-type-library-importer.md)
- [Výzvy příkazového řádku](developer-command-prompt-for-vs.md)
