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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 843b791177b57134483a7076dbc6ec979956ef60
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877220"
---
# <a name="tlbexpexe-type-library-exporter"></a>Tlbexp.exe (exportér knihovny typů)
Exportér knihovny typů generuje knihovny typů, které popisují typy definované v sestavení Common Language Runtime.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
tlbexp assemblyName [options]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*assemblyName*|Sestavení, pro které se má exportovat knihovna typů.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/asmpath:** *adresáře*|Určuje umístění, ve kterém se mají hledat sestavení. Pokud použijete tuto možnost, musíte explicitně zadat umístění, ve kterém se mají hledat odkazovaná sestavení, včetně aktuálního adresáře.<br /><br /> Při použití **asmpath** možnost, Exportér knihovny typů nebude hledat sestavení v globální mezipaměti sestavení (GAC).|  
|**/ Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/ názvy:** *název souboru*|Určuje velikost písmen názvů v knihovně typů. *Filename* argument je textový soubor. Každý řádek v souboru určuje velikost písmen jednoho názvu v knihovně typů.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/oldnames**|Donutí Tlbexp.exe exportovat upravené názvy typů, jestliže dojde ke konfliktu názvu typů. Toto bylo výchozí chování ve verzích rozhraní .NET Framework nižších než 2.0.|  
|**/ out:** *souboru*|Určuje název souboru knihovny typů, který má být vytvořen. Pokud tento parametr vynecháte, Tlbexp.exe vygeneruje knihovnu typů se stejným názvem, jako je název sestavení (skutečný název sestavení, který nemusí být nutně stejný jako název souboru obsahujícího sestavení), a s příponou .tlb.|  
|**/silence:** `warningnumber`|Potlačí zobrazení konkrétního upozornění. Tento parametr nelze použít s **/silent**.|  
|**/ silent**|Potlačí zobrazování zpráv o úspěšném dokončení. Tento parametr nelze použít s **/nečinnosti**.|  
|**/tlbreference:** *typelibraryname*|Donutí Tlbexp.exe explicitně vyřešit odkazy typu knihovny bez konzultace s registrem. Například, pokud sestavení B odkazuje na sestavení A, můžete použít tuto možnost k poskytnutí explicitního odkazu na knihovnu typů a nespoléhat se na knihovnu typů zadanou v registru. Tlbexp.exe provádí kontroly verze pro zajištění, že verze knihovny typů bude odpovídat verzi sestavení; pokud verze knihovny neodpovídá, dojde k chybě.<br /><br /> Všimněte si, že **tlbreference** možnost stále konzultaci s registrem v případech, kde <xref:System.Runtime.InteropServices.ComImportAttribute> atribut se aplikuje na rozhraní následně implementované jiným typem.|  
|**/tlbrefpath:** *cesta*|Plně kvalifikovaná cesta na odkazovanou knihovnu typů.|  
|**/ Win32**|Při kompilaci na 64bitovém počítači tato možnost určuje, že Tlbexp.exe vygeneruje 32bitovou knihovnu typů.|  
|**/Win64**|Při kompilaci na 32bitovém počítači tato možnost určuje, že Tlbexp.exe vygeneruje 64bitovou knihovnu typů.|  
|**/verbose**|Určuje režim podrobného vypisování; zobrazí seznam všech odkazovaných sestavení, pro která je třeba vytvořit knihovnu typů.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
> [!NOTE]
>  Možnosti příkazového řádku pro Tlbexp.exe nerozlišují malá a velká písmena a lze je zadat v libovolném pořadí. Pro jednoznačnou identifikaci je potřeba pouze poskytnout dostatek parametrů. Například **/n** je ekvivalentní **/nologo**, a **/o:** *outfile.tlb* je ekvivalentní **/out:**  *OutFile.tlb*.  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Tlbexp.exe vygeneruje knihovnu typů obsahující definice typů definovaných v sestavení. Aplikace jako například Visual Basic 6.0 může použít vygenerovanou knihovnu typů ke svázání s typy rozhraní .NET definovanými v sestavení.  
  
> [!IMPORTANT]
>  Pomocí nástroje Tlbexp.exe nelze exportovat soubory metadat systému Windows (.winmd). Export sestavení modulů Windows Runtime není podporován.  
  
 Celé sestavení se převede najednou. Pomocí nástroje Tlbexp.exe nelze generovat informace o typu pro podtypy definované v sestavení.  
  
 Tlbexp.exe nelze použít k vytvoření knihovny typů ze sestavení, která byla importována pomocí [Importér knihovny typů (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Místo toho byste měli použít původní knihovnu typů, která byla importována pomocí nástroje Tlbimp.exe. Knihovny typů můžete exportovat ze sestavení, která odkazují na sestavení, jež byla importována pomocí nástroje Tlbimp.exe. Příklady najdete v části níže.  
  
 Nástroj Tlbexp.exe umístí vytvořenou knihovnu typů do aktuálního pracovního adresáře nebo do adresáře určeného pro výstupní soubor. Jediné sestavení může způsobit vygenerování několika knihoven typů.  
  
 Nástroj Tlbexp.exe vygeneruje knihovnu typů, ale nezaregistruje ji. To je v kontrastu s [nástroj Assembly Registration (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md), který vygeneruje i zaregistruje knihovnu typů. Chcete-li vygenerovat a zaregistrovat knihovnu typů s modelem COM, použijte nástroj Regasm.exe.  
  
 Pokud nezadáte buď `/win32` nebo `/win64` možnost, Tlbexp.exe vygeneruje knihovnu typů 32bitová nebo 64bitová verze, která odpovídá typu počítače, na kterém provádíte kompilaci (32bitový nebo 64bitové počítače). Pro účely křížové kompilace můžete použít `/win64` možnost na 32bitovém počítači k vygenerování knihovny 64bitového typu a vy můžete použít `/win32` možnost Generovat knihovnu typů 32-bit na 64bitovém počítači. V knihovnách typů 32-bit <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> nastavena na hodnotu <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>. V knihovnách typů 64-bit <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> nastavena na hodnotu <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>. Všechny transformace datových typů (například typy velikosti ukazatelů dat, jako `IntPtr` a `UIntPtr`) se budou náležitě převedeny.  
  
 Pokud používáte <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributy <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> hodnotu `VT_UNKOWN` nebo `VT_DISPATCH`, Tlbexp.exe ignoruje jakékoli další použití <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> pole. Například při následujících podpisech:  
  
```  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_UNKNOWN, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructUnkSafe(){return null;}  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_DISPATCH, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructDispSafe(){return null;}  
```  
  
 je vygenerována následující knihovna typů:  
  
```  
[id(0x60020004)]  
HRESULT StructUnkSafe([out, retval] SAFEARRAY(IUnknown*)* pRetVal);  
[id(0x60020005)]  
HRESULT StructDispSafe([out, retval] SAFEARRAY(IDispatch*)* pRetVal);  
```  
  
 Všimněte si, že Tlbexp.exe ignoruje <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> pole.  
  
 Vzhledem k tomu, že knihovny typů nemohou pojmout všechny informace, které jsou součástí sestavení, nástroj Tlbexp.exe může zrušit některá data během exportu. Vysvětlení procesu transformace a identifikace zdroje každé dílčí informace, které jsou emitovány do knihovny typů, najdete v článku [sestavení pro souhrn převodu knihovny typů](https://msdn.microsoft.com/library/3a37eefb-a76c-4000-9080-7dbbf66a4896).  
  
 Všimněte si, že Exportér knihovny typů exportuje metody, které mají <xref:System.TypedReference> parametry jako `VARIANT`, i když <xref:System.TypedReference> objekt nemá v nespravovaném kódu žádný význam. Při exportu metod, které mají <xref:System.TypedReference> parametry, Exportér knihovny typů nebude generovat upozornění nebo chyby a nespravovaný kód využívající výslednou knihovnu typů nebude fungovat správně.  
  
 Exportér knihovny typů je podporován v systému Microsoft Windows 2000 a novějším.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vygeneruje knihovnu typů se stejným názvem jako sestavení v `myTest.dll`.  
  
```  
tlbexp myTest.dll  
```  
  
 Následující příkaz vygeneruje knihovnu typů s názvem `clipper.tlb`.  
  
```  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 Následující příklad ukazuje použití nástroje Tlbexp.exe k exportování knihovny typů ze sestavení, které odkazuje na sestavení, jež byla importována pomocí nástroje Tlbimp.exe.  
  
 Nejprve pomocí Tlbimp.exe importujte knihovny typů `myLib.tlb` a uložte ho jako `myLib.dll`.  
  
```  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 Následující příkaz využívá kompilátor jazyka C# ke kompilaci `Sample.dll,` odkazy `myLib.dll` vytvořili v předchozím příkladu.  
  
```  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 Následující příkaz vygeneruje knihovnu typů pro `Sample.dll` , která odkazuje na `myLib.dll`.  
  
```  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.TypeLibExporterFlags>  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Regasm.exe (nástroj registrace sestavení)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)  
 [Sestavení zadejte souhrn převodu knihovny](https://msdn.microsoft.com/library/3a37eefb-a76c-4000-9080-7dbbf66a4896)  
 [Tlbimp.exe (importér knihovny typů)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
