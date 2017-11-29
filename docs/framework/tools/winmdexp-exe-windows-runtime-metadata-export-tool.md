---
title: "Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4571d7576bc81432c87e0371ae0b6df3261f5f08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)
[!INCLUDE[wrt](../../../includes/wrt-md.md)] Metadata nástroj pro Export (Winmdexp.exe) transformuje modul rozhraní .NET Framework na soubor, který obsahuje [!INCLUDE[wrt](../../../includes/wrt-md.md)] metadat. I když sestavení rozhraní .NET Framework a [!INCLUDE[wrt](../../../includes/wrt-md.md)] soubory metadat použít stejný fyzický formát, jsou rozdíly v obsahu tabulky metadat, což znamená, že sestavení rozhraní .NET Framework nejsou automaticky použitelné jako [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti . Proces zapnutí modul do rozhraní .NET Framework [!INCLUDE[wrt](../../../includes/wrt-md.md)] součást se označuje jako *export*. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], bude výsledný soubor metadat (.winmd) systému Windows obsahuje metadata a implementace.  
  
 Při použití  **[!INCLUDE[wrt](../../../includes/wrt-md.md)] součást** šablony, která se nachází v **Windows Store** pro C# a Visual Basic v [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] nebo [!INCLUDE[vs_dev11_ext](../../../includes/vs-dev11-ext-md.md)], kompilátoru cíl je soubor .winmdobj a následné sestavení krok volá Winmdexp.exe export souboru .winmdobj .winmd souboru. Toto je doporučený způsob sestavení [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti. Jestliže chcete mít lepší kontrolu nad procesem sestavení, než jakou poskytuje sada Visual Studio, použijte přímo nástroj Winmdexp.exe.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
winmdexp [options] winmdmodule  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument nebo možnost|Popis|  
|------------------------|-----------------|  
|`winmdmodule`|Určuje modul (.winmdobj), který má být exportován. Je povolen pouze jeden modul. Chcete-li vytvořit tento modul, použijte `/target` – možnost kompilátoru s `winmdobj` cíl. V tématu [/target: winmdobj (možnosti kompilátoru C#)](~/docs/csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) nebo [/Target (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:``docfile`<br /><br /> `/d:``docfile`|Určuje výstupní soubor dokumentace XML, který bude vytvořen nástrojem Winmdexp.exe. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výstupní soubor je v podstatě stejný jako vstupní soubor XML dokumentace.|  
|`/moduledoc:``docfile`<br /><br /> `/md:``docfile`|Určuje název souboru dokumentace XML, který vytváří kompilátor s `winmdmodule`.|  
|`/modulepdb:``symbolfile`<br /><br /> `/mp:``symbolfile`|Určuje název souboru databáze (PDB) program, který obsahuje symboly pro `winmdmodule`.|  
|`/nowarn:``warning`|Potlačí zadané číslo upozornění. Pro *upozornění*, zadejte pouze číselnou část kód chyby bez nul.|  
|`/out:``file`<br /><br /> `/o:``file`|Určuje název výstupního souboru metadat Windows (.winmd).|  
|`/pdb:``symbolfile`<br /><br /> `/p:``symbolfile`|Určuje název výstupního souboru databáze programu (PDB), který bude obsahovat symboly pro exportovaný soubor metadat Windows (.winmd).|  
|`/reference:``winmd`<br /><br /> `/r:``winmd`|Určuje referenční soubor metadat (.winmd nebo sestavení) používaný při exportu. Pokud používáte referenční sestavení v "\Program soubory (x86) \Reference Assemblies\Microsoft\Framework\\. NETCore\v4.5 "(" \Program Files\\... "na 32bitové počítače), nezahrnují odkazy na System.Runtime.dll i mscorlib.dll.|  
|`/utf8output`|Určuje, že výstupní zpráva má být v kódování UTF-8.|  
|`/warnaserror+`|Určuje, že všechna upozornění mají být považována za chyby.|  
|**@** `responsefile`|Určuje soubor odezvy (.rsp), který obsahuje možnosti (a volitelně `winmdmodule`). Každý řádek v `responsefile` musí obsahovat jeden argument, nebo možnost.|  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Winmdexp.exe není určen pro převod libovolného sestavení rozhraní .NET Framework na soubor .winmd. Vyžaduje modul, který je kompilovat s `/target:winmdobj` možnost a další omezení platí. Nejdůležitější těchto omezení je, že musí být všechny typy, které jsou zveřejněné v plochy rozhraní API sestavení [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy. Další informace najdete v části "Deklarace typy v prostředí Windows Runtime komponenty" článku [vytváření součásti systému Windows Runtime v C# a Visual Basic](http://go.microsoft.com/fwlink/p/?LinkID=238313) ve službě Windows Dev Center.  
  
 Při psaní [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace nebo [!INCLUDE[wrt](../../../includes/wrt-md.md)] součást s C# nebo Visual Basic, rozhraní .NET Framework poskytuje podporu, aby programování s [!INCLUDE[wrt](../../../includes/wrt-md.md)] přirozenější. To je popsána v článku [rozhraní .NET Framework podporu pro aplikace Windows Store a prostředí Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). V procesu, některé nejčastěji používané [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy jsou namapovány na typy rozhraní .NET Framework. Winmdexp.exe obrátí tento proces a vytváří plochy rozhraní API, která používá k odpovídající položce [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy. Například typy, které se vytvářejí na základě <xref:System.Collections.Generic.IList%601> mapy rozhraní pro typy, které se vytvářejí na základě [!INCLUDE[wrt](../../../includes/wrt-md.md)] [IVector\<T >](http://go.microsoft.com/fwlink/p/?LinkId=251132)rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Podpora v rozhraní .NET framework pro aplikace pro Windows Store a prostředí Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
 [Vytváření modulu Runtime součásti systému Windows v C# a Visual Basic](http://go.microsoft.com/fwlink/p/?LinkID=238313)  
 [Winmdexp.exe chybové zprávy](../../../docs/framework/tools/winmdexp-exe-error-messages.md)  
 [Sestavení, nasazení a nástroje pro konfiguraci (rozhraní .NET Framework)](http://msdn.microsoft.com/en-us/b8c921be-6012-4181-b8d4-ab15813fc9a7)
