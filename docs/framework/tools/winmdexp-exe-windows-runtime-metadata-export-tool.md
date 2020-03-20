---
title: Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
ms.openlocfilehash: 52820b78f6ed7b02e80df66f90a01143b31d9b29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74447276"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)
Nástroj Pro export metadat prostředí Windows Runtime (Winmdexp.exe) transformuje modul rozhraní .NET Framework do souboru, který obsahuje metadata prostředí Windows Runtime. Přestože sestavení rozhraní .NET Framework a soubory metadat prostředí Windows Runtime používají stejný fyzický formát, existují rozdíly v obsahu tabulek metadat, což znamená, že sestavení rozhraní .NET Framework nejsou automaticky použitelná jako součásti prostředí Windows Runtime . Proces přeměny modulu rozhraní .NET Framework na součást prostředí Windows Runtime se označuje jako *export*. V rozhraních .NET Framework 4.5 a .NET Framework 4.5.1 obsahuje výsledný soubor metadat systému Windows (.winmd) metadata i implementaci.  
  
 Při použití šablony **komponenty Prostředí Windows Runtime,** která je umístěna v **rámci Windows Store** pro C# a Visual Basic v sadě Visual Studio 2013 nebo Visual Studio 2012, je cílem kompilátoru soubor Winmdobj a následující krok sestavení volá winmdexp.exe k exportu souboru Winmdobj do souboru WINMD. Toto je doporučený způsob vytvoření součásti prostředí Windows Runtime. Jestliže chcete mít lepší kontrolu nad procesem sestavení, než jakou poskytuje sada Visual Studio, použijte přímo nástroj Winmdexp.exe.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument nebo možnost|Popis|  
|------------------------|-----------------|  
|`winmdmodule`|Určuje modul (.winmdobj), který má být exportován. Je povolen pouze jeden modul. Chcete-li vytvořit tento `/target` modul, použijte `winmdobj` možnost kompilátoru s cílem. Viz [-target:winmdobj (C# Compiler Options)](../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) nebo [-target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:` `docfile`<br /><br /> `/d:` `docfile`|Určuje výstupní soubor dokumentace XML, který bude vytvořen nástrojem Winmdexp.exe. V rozhraní .NET Framework 4.5 je výstupní soubor v podstatě stejný jako vstupní soubor dokumentace XML.|  
|`/moduledoc:` `docfile`<br /><br /> `/md:` `docfile`|Určuje název souboru dokumentace XML, který kompilátor vytvořil s `winmdmodule`.|  
|`/modulepdb:` `symbolfile`<br /><br /> `/mp:` `symbolfile`|Určuje název souboru databáze programů (PDB), který `winmdmodule`obsahuje symboly pro .|  
|`/nowarn:` `warning`|Potlačí zadané číslo upozornění. Pro *upozornění*zajistěte pouze číselnou část kódu chyby bez úvodních nul.|  
|`/out:` `file`<br /><br /> `/o:` `file`|Určuje název výstupního souboru metadat Windows (.winmd).|  
|`/pdb:` `symbolfile`<br /><br /> `/p:` `symbolfile`|Určuje název výstupního souboru databáze programu (PDB), který bude obsahovat symboly pro exportovaný soubor metadat Windows (.winmd).|  
|`/reference:` `winmd`<br /><br /> `/r:` `winmd`|Určuje referenční soubor metadat (.winmd nebo sestavení) používaný při exportu. Používáte-li referenční sestavení v části \Program Files (x86)\Reference\\Assemblies\Microsoft\Framework . NETCore\v4.5" ("\Programové soubory\\..." 32bitových počítačích) obsahují odkazy na souborSystem.Runtime.dll i mscorlib.dll.|  
|`/utf8output`|Určuje, že výstupní zpráva má být v kódování UTF-8.|  
|`/warnaserror+`|Určuje, že všechna upozornění mají být považována za chyby.|  
|**@** `responsefile`|Určuje soubor odpovědi (.rsp), který obsahuje volby (a volitelně `winmdmodule`). Každý řádek `responsefile` v by měl obsahovat jeden argument nebo možnost.|  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Winmdexp.exe není určen pro převod libovolného sestavení rozhraní .NET Framework na soubor .winmd. Vyžaduje modul, který je kompilován s `/target:winmdobj` možností a platí další omezení. Nejdůležitější z těchto omezení je, že všechny typy, které jsou vystaveny v povrchu rozhraní API sestavení musí být typy prostředí Windows Runtime. Další informace naleznete v části Deklarování typů v součástech prostředí Windows Runtime v článku [Vytváření součástí prostředí Windows Runtime v jazyce C# a visual basicu](https://docs.microsoft.com/previous-versions/br230301(v=vs.110)).
  
 Při psaní aplikace pro Windows 8.x Store nebo součásti Prostředí Windows Runtime s c# nebo Visual Basic, rozhraní .NET Framework poskytuje podporu, aby programování s prostředím Windows Runtime bylo přirozenější. To je popsáno v článku [.NET Framework Support pro Aplikace pro Windows Store a prostředí Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). V procesu jsou některé běžně používané typy prostředí Windows Runtime mapovány na typy rozhraní .NET Framework. Program Winmdexp.exe tento proces obrátí a vytvoří povrch rozhraní API, který používá odpovídající typy prostředí Windows Runtime. Například typy, které jsou <xref:System.Collections.Generic.IList%601> vytvořeny z mapy rozhraní na typy, <xref:Windows.Foundation.Collections.IVector%601> které jsou vytvořeny z rozhraní prostředí Windows Runtime.  
  
## <a name="see-also"></a>Viz také

- [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Vytváření součástí prostředí Windows Runtime v jazyce C# a jazyce Visual Basic](https://docs.microsoft.com/previous-versions/br230301(v=vs.110))
- [Chybové zprávy nástroje Winmdexp.exe](winmdexp-exe-error-messages.md)
- [Nástroje pro sestavení, nasazení a konfiguraci (rozhraní.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
