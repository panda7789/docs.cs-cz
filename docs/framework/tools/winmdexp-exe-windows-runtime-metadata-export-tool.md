---
title: Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5803ef1d174c3e3a5e8e18b130e6b7a0c65eac81
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216338"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)
[!INCLUDE[wrt](../../../includes/wrt-md.md)] Metadata Export Tool (Winmdexp.exe) převede modul rozhraní .NET Framework na soubor, který obsahuje [!INCLUDE[wrt](../../../includes/wrt-md.md)] metadat. Přestože sestavení rozhraní .NET Framework a [!INCLUDE[wrt](../../../includes/wrt-md.md)] soubory metadat použít stejný fyzický formát, existují rozdíly v obsahu tabulek metadat, což znamená, že sestavení rozhraní .NET Framework nejsou automaticky použitelná jako [!INCLUDE[wrt](../../../includes/wrt-md.md)] komponenty . Proces přeměny modulu rozhraní .NET Framework do [!INCLUDE[wrt](../../../includes/wrt-md.md)] komponenty se označuje jako *export*. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], výsledný soubor Windows metadata (.winmd) obsahuje metadata i implementaci.  
  
 Při použití  **[!INCLUDE[wrt](../../../includes/wrt-md.md)] komponenty** šablonu, která je umístěna ve složce **Windows Store** pro C# a Visual Basic v sadě Visual Studio 2013 nebo Visual Studio 2012, je cílem kompilátoru soubor .winmdobj, a následný krok sestavení zavolá Winmdexp.exe exportu souboru .winmdobj do souboru .winmd. Toto je doporučený způsob sestavení [!INCLUDE[wrt](../../../includes/wrt-md.md)] komponenty. Jestliže chcete mít lepší kontrolu nad procesem sestavení, než jakou poskytuje sada Visual Studio, použijte přímo nástroj Winmdexp.exe.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument nebo možnost|Popis|  
|------------------------|-----------------|  
|`winmdmodule`|Určuje modul (.winmdobj), který má být exportován. Je povolen pouze jeden modul. Chcete-li vytvořit tento modul, použijte `/target` – možnost kompilátoru s `winmdobj` cíl. Zobrazit [/target: winmdobj (možnosti kompilátoru C#)](~/docs/csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) nebo [/Target (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:` `docfile`<br /><br /> `/d:` `docfile`|Určuje výstupní soubor dokumentace XML, který bude vytvořen nástrojem Winmdexp.exe. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výstupní soubor je v podstatě stejný jako vstupní soubor dokumentace XML.|  
|`/moduledoc:` `docfile`<br /><br /> `/md:` `docfile`|Určuje název souboru dokumentace XML, který kompilátor vytvořil pomocí `winmdmodule`.|  
|`/modulepdb:` `symbolfile`<br /><br /> `/mp:` `symbolfile`|Určuje název souboru databáze (PDB) program, který obsahuje symboly pro `winmdmodule`.|  
|`/nowarn:` `warning`|Potlačí zadané číslo upozornění. Pro *upozornění*, zadejte pouze číselnou část chybového kódu bez počátečních nul.|  
|`/out:` `file`<br /><br /> `/o:` `file`|Určuje název výstupního souboru metadat Windows (.winmd).|  
|`/pdb:` `symbolfile`<br /><br /> `/p:` `symbolfile`|Určuje název výstupního souboru databáze programu (PDB), který bude obsahovat symboly pro exportovaný soubor metadat Windows (.winmd).|  
|`/reference:` `winmd`<br /><br /> `/r:` `winmd`|Určuje referenční soubor metadat (.winmd nebo sestavení) používaný při exportu. Pokud použijete referenční sestavení v "\Program soubory (x86) \Reference Assemblies\Microsoft\Framework\\. NETCore\v4.5 "(" \Program Files\\... "na 32bitových počítačích), zahrnují odkazy na knihovnu System.Runtime.dll i mscorlib.dll.|  
|`/utf8output`|Určuje, že výstupní zpráva má být v kódování UTF-8.|  
|`/warnaserror+`|Určuje, že všechna upozornění mají být považována za chyby.|  
|**@** `responsefile`|Určuje soubor odpovědí (.rsp) obsahující možnosti (a volitelně `winmdmodule`). Každý řádek v `responsefile` by měl obsahovat jeden argument nebo parametr.|  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Winmdexp.exe není určen pro převod libovolného sestavení rozhraní .NET Framework na soubor .winmd. Vyžaduje modul zkompilovaný pomocí `/target:winmdobj` možnost a další omezení platí. Nejdůležitější z těchto omezení je, že všechny typy, které jsou vystaveny na povrchu API sestavení musí být [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy. Další informace najdete v tématu "Deklarace typů součástí prostředí Windows Runtime" v článku [vytváření komponent Windows Runtime v jazyce C# a Visual Basic](https://go.microsoft.com/fwlink/p/?LinkID=238313) Windows Dev Center.  
  
 Při psaní [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace nebo [!INCLUDE[wrt](../../../includes/wrt-md.md)] součástí s použitím jazyka C# nebo Visual Basic, rozhraní .NET Framework poskytuje podporu pro programování v jazyce [!INCLUDE[wrt](../../../includes/wrt-md.md)] přirozenější. Tento postup je popsán v článku [podpory pro Windows Store aplikací využívajících .NET Framework a prostředí Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). V procesu, některé běžně používané [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy jsou mapovány na typy rozhraní .NET Framework. Winmdexp.exe Tento proces obrací a vytváří povrch rozhraní API využívající odpovídající [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy. Například typy, které jsou zhotoveny z <xref:System.Collections.Generic.IList%601> mapy rozhraní pro typy, které jsou zhotoveny z [!INCLUDE[wrt](../../../includes/wrt-md.md)] [IVector\<T >](https://go.microsoft.com/fwlink/p/?LinkId=251132)rozhraní.  
  
## <a name="see-also"></a>Viz také:

- [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Vytváření komponent Windows Runtime v jazyce C# a Visual Basic](https://go.microsoft.com/fwlink/p/?LinkID=238313)
- [Chybové zprávy nástroje Winmdexp.exe](../../../docs/framework/tools/winmdexp-exe-error-messages.md)
- [Nástroje pro sestavování, nasazení a konfiguraci (.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
