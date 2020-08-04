---
title: Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)
description: Pochopení Winmdexp.exe nástroje pro export metadat prostředí Windows Runtime. Tento nástroj transformuje modul .NET do souboru, který obsahuje metadata prostředí Windows Runtime.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
ms.openlocfilehash: 10626e00eb340d84653419da18a0b219ef1d197e
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517019"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)
Nástroj pro export metadat prostředí Windows Runtime (Winmdexp.exe) transformuje modul .NET Framework na soubor, který obsahuje metadata prostředí Windows Runtime. I když .NET Framework sestavení a prostředí Windows Runtime soubory metadat používají stejný fyzický formát, existují rozdíly v obsahu tabulek metadat, což znamená, že .NET Framework sestavení nejsou automaticky použitelná jako prostředí Windows Runtime Components. Proces zapnutí modulu .NET Framework do prostředí Windows Runtime komponenty se označuje jako *Export*. V .NET Framework 4,5 a .NET Framework 4.5.1 výsledný soubor metadat Windows (. winmd) obsahuje metadata i implementaci.  
  
 Použijete-li šablonu **prostředí Windows Runtime komponenty** , která je umístěna v části **Windows Store** pro C# a Visual Basic v Visual Studio 2013 nebo Visual Studio 2012, je cílem kompilátoru soubor. winmdobj a následný krok sestavení volá Winmdexp.exe pro export souboru. winmdobj do souboru. winmd. Toto je doporučený způsob, jak vytvořit součást prostředí Windows Runtime. Jestliže chcete mít lepší kontrolu nad procesem sestavení, než jakou poskytuje sada Visual Studio, použijte přímo nástroj Winmdexp.exe.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument nebo možnost|Description|  
|------------------------|-----------------|  
|`winmdmodule`|Určuje modul (.winmdobj), který má být exportován. Je povolen pouze jeden modul. Chcete-li vytvořit tento modul, použijte `/target` možnost kompilátoru s `winmdobj` cílem. Viz [-target: winmdobj (možnosti kompilátoru C#)](../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) nebo [-target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:` `docfile`<br /><br /> `/d:` `docfile`|Určuje výstupní soubor dokumentace XML, který bude vytvořen nástrojem Winmdexp.exe. V .NET Framework 4,5 je výstupní soubor v podstatě stejný jako vstupní soubor dokumentace XML.|  
|`/moduledoc:` `docfile`<br /><br /> `/md:` `docfile`|Určuje název souboru dokumentace XML, pomocí kterého kompilátor vytvořil `winmdmodule` .|  
|`/modulepdb:` `symbolfile`<br /><br /> `/mp:` `symbolfile`|Určuje název souboru programu databáze programu (PDB), který obsahuje symboly pro `winmdmodule` .|  
|`/nowarn:` `warning`|Potlačí zadané číslo upozornění. Pro *Upozornění*zadejte pouze číselnou část kódu chyby bez úvodní nuly.|  
|`/out:` `file`<br /><br /> `/o:` `file`|Určuje název výstupního souboru metadat Windows (.winmd).|  
|`/pdb:` `symbolfile`<br /><br /> `/p:` `symbolfile`|Určuje název výstupního souboru databáze programu (PDB), který bude obsahovat symboly pro exportovaný soubor metadat Windows (.winmd).|  
|`/reference:` `winmd`<br /><br /> `/r:` `winmd`|Určuje referenční soubor metadat (.winmd nebo sestavení) používaný při exportu. Použijete-li referenční sestavení v umístění "\Program Files (x86) \Reference Assemblies\Microsoft\Framework \\ . NETCore\v4.5 "(" \Program Files \\ ... " v 32 počítačích) zahrňte odkazy na System.Runtime.dll i mscorlib.dll.|  
|`/utf8output`|Určuje, že výstupní zpráva má být v kódování UTF-8.|  
|`/warnaserror+`|Určuje, že všechna upozornění mají být považována za chyby.|  
|**@** `responsefile`|Určuje soubor odpovědi (. rsp), který obsahuje možnosti (a volitelně `winmdmodule` ). Každý řádek v `responsefile` by měl obsahovat jeden argument nebo možnost.|  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Winmdexp.exe není určen pro převod libovolného sestavení rozhraní .NET Framework na soubor .winmd. Vyžaduje modul kompilovaný s `/target:winmdobj` možností a platí další omezení. Nejdůležitější z těchto omezení je, že všechny typy, které jsou vystaveny na povrchu rozhraní API sestavení, musí být prostředí Windows Runtime typy. Další informace naleznete v části "deklarace typů v prostředí Windows Runtimech součástech" [v článku vytváření prostředí Windows Runtime komponent v jazyce C# a Visual Basic](https://docs.microsoft.com/previous-versions/br230301(v=vs.110)).
  
 Když napíšete aplikaci Windows 8. x Store nebo komponentu prostředí Windows Runtime v jazyce C# nebo Visual Basic, .NET Framework poskytuje podporu k vytváření dalších prostředí Windows Runtime přirozeného programování. Tento článek je popsán v článku [.NET Framework podpoře aplikací pro Windows Store a prostředí Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). V procesu jsou některé běžně používané typy prostředí Windows Runtime namapovány na .NET Framework typy. Winmdexp.exe tento proces obrátí a vytvoří plochu rozhraní API, která používá odpovídající typy prostředí Windows Runtime. Například typy, které jsou vytvořeny z <xref:System.Collections.Generic.IList%601> mapy rozhraní na typy, které jsou sestaveny z rozhraní prostředí Windows Runtime <xref:Windows.Foundation.Collections.IVector%601> .  
  
## <a name="see-also"></a>Viz také

- [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Vytváření komponent prostředí Windows Runtime v jazyce C# a Visual Basic](https://docs.microsoft.com/previous-versions/br230301(v=vs.110))
- [Winmdexp.exe chybové zprávy](winmdexp-exe-error-messages.md)
- [Sestavování, nasazování a Konfigurační nástroje (.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
