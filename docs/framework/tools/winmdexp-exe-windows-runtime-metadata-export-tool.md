---
title: Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ce98912e579e0dd570822c1f7c2133bb05ed491
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773970"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)
Nástroj pro export metadat prostředí Windows Runtime (Winmdexp. exe) transformuje modul .NET Framework na soubor, který obsahuje prostředí Windows Runtime metadata. I když .NET Framework sestavení a prostředí Windows Runtime soubory metadat používají stejný fyzický formát, existují rozdíly v obsahu tabulek metadat, což znamená, že .NET Framework sestavení nejsou automaticky použitelná jako prostředí Windows Runtime komponenty . Proces zapnutí modulu .NET Framework do prostředí Windows Runtime komponenty se označuje jako *Export*. V .NET Framework 4,5 a .NET Framework 4.5.1 výsledný soubor metadat Windows (. winmd) obsahuje metadata i implementaci.  
  
 Použijete-li šablonu **prostředí Windows Runtime komponenty** , která je umístěna v části **Windows Store** pro C# a Visual Basic v Visual Studio 2013 nebo Visual Studio 2012, je cílem kompilátoru soubor. winmdobj a následné volání kroků sestavení Winmdexp. exe pro export souboru. winmdobj do souboru. winmd. Toto je doporučený způsob, jak vytvořit součást prostředí Windows Runtime. Jestliže chcete mít lepší kontrolu nad procesem sestavení, než jakou poskytuje sada Visual Studio, použijte přímo nástroj Winmdexp.exe.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument nebo možnost|Popis|  
|------------------------|-----------------|  
|`winmdmodule`|Určuje modul (.winmdobj), který má být exportován. Je povolen pouze jeden modul. Chcete-li vytvořit tento modul, použijte možnost kompilátoru `/target` s cílem `winmdobj`. Viz [-target: winmdobj (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) nebo [-target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:``docfile`<br /><br /> `/d:``docfile`|Určuje výstupní soubor dokumentace XML, který bude vytvořen nástrojem Winmdexp.exe. V .NET Framework 4,5 je výstupní soubor v podstatě stejný jako vstupní soubor dokumentace XML.|  
|`/moduledoc:``docfile`<br /><br /> `/md:``docfile`|Určuje název souboru dokumentace XML, který kompilátor vytvořil pomocí `winmdmodule`.|  
|`/modulepdb:``symbolfile`<br /><br /> `/mp:``symbolfile`|Určuje název souboru programu databáze programu (PDB), který obsahuje symboly pro `winmdmodule`.|  
|`/nowarn:``warning`|Potlačí zadané číslo upozornění. Pro *Upozornění*zadejte pouze číselnou část kódu chyby bez úvodní nuly.|  
|`/out:``file`<br /><br /> `/o:``file`|Určuje název výstupního souboru metadat Windows (.winmd).|  
|`/pdb:``symbolfile`<br /><br /> `/p:``symbolfile`|Určuje název výstupního souboru databáze programu (PDB), který bude obsahovat symboly pro exportovaný soubor metadat Windows (.winmd).|  
|`/reference:``winmd`<br /><br /> `/r:``winmd`|Určuje referenční soubor metadat (.winmd nebo sestavení) používaný při exportu. Použijete-li referenční sestavení v "\Program Files (x86) \Reference Assemblies\Microsoft\Framework \\. NETCore\v4.5" ("\Program Files \\..." v 32ch počítačích), zahrňte odkazy na System. Runtime. dll i mscorlib. dll.|  
|`/utf8output`|Určuje, že výstupní zpráva má být v kódování UTF-8.|  
|`/warnaserror+`|Určuje, že všechna upozornění mají být považována za chyby.|  
|**@** `responsefile`|Určuje soubor odpovědi (. rsp), který obsahuje možnosti (a volitelně `winmdmodule`). Každý řádek v `responsefile` by měl obsahovat jeden argument nebo možnost.|  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Winmdexp.exe není určen pro převod libovolného sestavení rozhraní .NET Framework na soubor .winmd. Vyžaduje modul kompilovaný s možností `/target:winmdobj` a platí další omezení. Nejdůležitější z těchto omezení je, že všechny typy, které jsou vystaveny na povrchu rozhraní API sestavení, musí být prostředí Windows Runtime typy. Další informace naleznete v části "deklarace typů v prostředí Windows Runtimech součástech" v článku [vytvoření prostředí Windows runtimech komponent v C# nástroji a Visual Basic](https://go.microsoft.com/fwlink/p/?LinkID=238313) na stránce Windows Dev Center.  
  
 Když napíšete [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikaci nebo komponentu prostředí Windows Runtime pomocí C# nástroje nebo Visual Basic, .NET Framework poskytuje podporu k vytváření dalších prostředí Windows runtimech přirozených způsobů programování. Tento článek je popsán v článku [.NET Framework podpoře aplikací pro Windows Store a prostředí Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). V procesu jsou některé běžně používané typy prostředí Windows Runtime namapovány na .NET Framework typy. Winmdexp. exe Tento proces vrátí a vytvoří plochu rozhraní API, která používá odpovídající typy prostředí Windows Runtime. Například typy, které jsou vytvořeny z mapování <xref:System.Collections.Generic.IList%601> rozhraní na typy, které jsou vytvořeny z rozhraní prostředí Windows Runtime[IVector \<T >](https://go.microsoft.com/fwlink/p/?LinkId=251132).  
  
## <a name="see-also"></a>Viz také:

- [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Vytváření komponent prostředí Windows Runtime v C# nástroji a Visual Basic](https://go.microsoft.com/fwlink/p/?LinkID=238313)
- [Chybové zprávy nástroje Winmdexp.exe](winmdexp-exe-error-messages.md)
- [Sestavování, nasazování a Konfigurační nástroje (.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
