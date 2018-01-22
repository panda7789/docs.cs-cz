---
title: "Tlbexp.exe (exportér knihovny typů)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting type library [.NET Framework]
- exporter tool [.NET Framework]
- Tlbexp.exe
- Type Library Exporter
- type libraries [.NET Framework], exporting
ms.assetid: a487d61b-d166-467b-a7ca-d8b52fbff42d
caps.latest.revision: "35"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47710b81de79a9dfbb6bddd39035be2986350b0e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="tlbexpexe-type-library-exporter"></a>Tlbexp.exe (exportér knihovny typů)
Exportér knihovny typů generuje knihovny typů, které popisují typy definované v sestavení Common Language Runtime.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
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
|**/asmpath:** *adresáře*|Určuje umístění, ve kterém se mají hledat sestavení. Pokud použijete tuto možnost, musíte explicitně zadat umístění, ve kterém se mají hledat odkazovaná sestavení, včetně aktuálního adresáře.<br /><br /> Při použití **asmpath** možnost, knihovna typů – Exportér nebude hledat sestavení v globální mezipaměti sestavení (GAC).|  
|**/help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/ názvy:** *filename*|Určuje velikost písmen názvů v knihovně typů. *Filename* argument je textový soubor. Každý řádek v souboru určuje velikost písmen jednoho názvu v knihovně typů.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/oldnames**|Donutí Tlbexp.exe exportovat upravené názvy typů, jestliže dojde ke konfliktu názvu typů. Toto bylo výchozí chování ve verzích rozhraní .NET Framework nižších než 2.0.|  
|**/ out:** *souboru*|Určuje název souboru knihovny typů, který má být vytvořen. Pokud tento parametr vynecháte, Tlbexp.exe vygeneruje knihovnu typů se stejným názvem, jako je název sestavení (skutečný název sestavení, který nemusí být nutně stejný jako název souboru obsahujícího sestavení), a s příponou .tlb.|  
|**/ nečinnosti:**`warningnumber`|Potlačí zobrazení konkrétního upozornění. Tuto možnost nelze použít s **/tichou**.|  
|**/ tichou**|Potlačí zobrazování zpráv o úspěšném dokončení. Tuto možnost nelze použít s **/ticho**.|  
|**/tlbreference:** *typelibraryname*|Donutí Tlbexp.exe explicitně vyřešit odkazy typu knihovny bez konzultace s registrem. Například, pokud sestavení B odkazuje na sestavení A, můžete použít tuto možnost k poskytnutí explicitního odkazu na knihovnu typů a nespoléhat se na knihovnu typů zadanou v registru. Tlbexp.exe provádí kontroly verze pro zajištění, že verze knihovny typů bude odpovídat verzi sestavení; pokud verze knihovny neodpovídá, dojde k chybě.<br /><br /> Všimněte si, že **tlbreference** možnost stále zajímají registru v případech, kde <xref:System.Runtime.InteropServices.ComImportAttribute> je použit atribut rozhraní, které je pak realizován pomocí jiného typu.|  
|**/tlbrefpath:** *path*|Plně kvalifikovaná cesta na odkazovanou knihovnu typů.|  
|**/win32**|Při kompilaci na 64bitovém počítači tato možnost určuje, že Tlbexp.exe vygeneruje 32bitovou knihovnu typů.|  
|**/win64**|Při kompilaci na 32bitovém počítači tato možnost určuje, že Tlbexp.exe vygeneruje 64bitovou knihovnu typů.|  
|**/verbose**|Určuje režim podrobného vypisování; zobrazí seznam všech odkazovaných sestavení, pro která je třeba vytvořit knihovnu typů.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
> [!NOTE]
>  Možnosti příkazového řádku pro Tlbexp.exe nerozlišují malá a velká písmena a lze je zadat v libovolném pořadí. Pro jednoznačnou identifikaci je potřeba pouze poskytnout dostatek parametrů. Například  **/n**  je ekvivalentní **/nologo**, a **/o:** *outfile.tlb* je ekvivalentní   **/out:**  *outfile.tlb*.  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Tlbexp.exe vygeneruje knihovnu typů obsahující definice typů definovaných v sestavení. Aplikace jako například Visual Basic 6.0 může použít vygenerovanou knihovnu typů ke svázání s typy rozhraní .NET definovanými v sestavení.  
  
> [!IMPORTANT]
>  Pomocí nástroje Tlbexp.exe nelze exportovat soubory metadat systému Windows (.winmd). Export sestavení modulů Windows Runtime není podporován.  
  
 Celé sestavení se převede najednou. Pomocí nástroje Tlbexp.exe nelze generovat informace o typu pro podtypy definované v sestavení.  
  
 Tlbexp.exe nelze použít k vytvoření knihovny typů ze sestavení, který byl importován pomocí [Importér knihovny typů (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Místo toho byste měli použít původní knihovnu typů, která byla importována pomocí nástroje Tlbimp.exe. Knihovny typů můžete exportovat ze sestavení, která odkazují na sestavení, jež byla importována pomocí nástroje Tlbimp.exe. Příklady najdete v části níže.  
  
 Nástroj Tlbexp.exe umístí vytvořenou knihovnu typů do aktuálního pracovního adresáře nebo do adresáře určeného pro výstupní soubor. Jediné sestavení může způsobit vygenerování několika knihoven typů.  
  
 Nástroj Tlbexp.exe vygeneruje knihovnu typů, ale nezaregistruje ji. To je rozdíl k [nástroj Assembly Registration (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md), který generuje i zaregistruje knihovny typů. Chcete-li vygenerovat a zaregistrovat knihovnu typů s modelem COM, použijte nástroj Regasm.exe.  
  
 Pokud nezadáte buď `/win32` nebo `/win64` možnost, Tlbexp.exe generuje knihovny typů 32bitovou nebo 64bitovou odpovídající typ počítače, na kterém provádíte kompilace (32bitový nebo 64bitový počítač). Pro účely mezi kompilace, můžete použít `/win64` můžete použít možnost na 32bitový počítač pro generování knihovny typů 64-bit a můžete `/win32` možnost na 64bitovém počítači k vygenerování knihovny typů 32-bit. V 32bitové typu knihovny <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> nastavena na hodnotu <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>. V typu 64-bit knihovny <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> nastavena na hodnotu <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>. Všechna data zadejte transformace (například velikost ukazatel datové typy, jako `IntPtr` a `UIntPtr`) se převedou správně.  
  
 Pokud použijete <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut k určení <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> hodnotu `VT_UNKOWN` nebo `VT_DISPATCH`, Tlbexp.exe ignoruje jakékoli následné použití <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> pole. Například při následujících podpisech:  
  
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
  
 Všimněte si, že ignoruje Tlbexp.exe <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> pole.  
  
 Vzhledem k tomu, že knihovny typů nemohou pojmout všechny informace, které jsou součástí sestavení, nástroj Tlbexp.exe může zrušit některá data během exportu. Proces transformace vysvětlení a identifikaci zdroje jednotlivé informace vygenerované do knihovny typů najdete v tématu [sestavení souhrn konverze typu knihovny](http://msdn.microsoft.com/library/3a37eefb-a76c-4000-9080-7dbbf66a4896).  
  
 Všimněte si, že knihovna typů – Exportér exportuje metody, které mají <xref:System.TypedReference> parametry jako `VARIANT`, i když <xref:System.TypedReference> objekt nemá význam v nespravovaném kódu. Při exportu metody, které mají <xref:System.TypedReference> parametry, knihovna typů – Exportér nebude generovat upozornění nebo chyby a nespravovaného kódu, který používá knihovnu výsledný typ nebude pracovat správně.  
  
 Exportér knihovny typů je podporován v systému Microsoft Windows 2000 a novějším.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vygeneruje typ knihovny se stejným názvem jako sestavení v `myTest.dll`.  
  
```  
tlbexp myTest.dll  
```  
  
 Následující příkaz vytvoří knihovny typů s názvem `clipper.tlb`.  
  
```  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 Následující příklad ukazuje použití nástroje Tlbexp.exe k exportování knihovny typů ze sestavení, které odkazuje na sestavení, jež byla importována pomocí nástroje Tlbimp.exe.  
  
 Nejprve pomocí Tlbimp.exe import knihovny typů `myLib.tlb` a uložte ho jako `myLib.dll`.  
  
```  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 Následující příkaz používá kompilátor jazyka C# pro kompilaci `Sample.dll,` odkazy `myLib.dll` vytvořili v předchozím příkladu.  
  
```  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 Následující příkaz vytvoří knihovnu typů pro `Sample.dll` odkazující `myLib.dll`.  
  
```  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.TypeLibExporterFlags>  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Regasm.exe (nástroj registrace sestavení)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)  
 [Sestavení na typ souhrn konverze knihovny](http://msdn.microsoft.com/library/3a37eefb-a76c-4000-9080-7dbbf66a4896)  
 [Tlbimp.exe (importér knihovny typů)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
