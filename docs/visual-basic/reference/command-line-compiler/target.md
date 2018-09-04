---
title: -target (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17528bb9faf137029b35e4a9f28bab7a28ae25db
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542255"
---
# <a name="-target-visual-basic"></a>-target (Visual Basic)
Určuje formát výstupu kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>Poznámky  
 Následující tabulka shrnuje vliv `-target` možnost.  
  
|**Možnost**|**Chování**|  
|----------------|------------------|  
|`-target:exe`|Způsobí, že kompilátor vytvoří spustitelný soubor konzoly aplikace.<br /><br /> Toto je výchozí možnost, pokud žádný `-target` je zadána možnost. Spustitelný soubor se vytvoří s příponou .exe.<br /><br /> Pokud není uvedeno jinak se `/out` možnost, název výstupního souboru přebírá název vstupního souboru, který obsahuje `Sub Main` postup.<br /><br /> Pouze jeden `Sub Main` postup je požadován v souborech zdrojového kódu, které jsou kompilovány do souboru s příponou .exe. Použití `-main` – možnost kompilátoru k určení, která třída obsahuje `Sub Main` postup.|  
|`-target:library`|Způsobí, že kompilátor vytvoří dynamickou knihovnu (DLL).<br /><br /> Je vytvořen soubor dynamické knihovny s příponou .dll.<br /><br /> Pokud není uvedeno jinak se `-out` možnost, název výstupního souboru využívá názvu prvního vstupního souboru.<br /><br /> Při sestavování knihovny DLL `Sub Main` postup není nutný.|  
|`-target:module`|Způsobí, že kompilátor generuje modul, který lze přidat do sestavení.<br /><br /> Vytvořil výstupní soubor s příponou .netmodule.<br /><br /> Modul common language runtime rozhraní .NET nelze načíst soubor, který nemá žádné sestavení. Tento soubor je však můžete začlenit do sestavení manifestu sestavení s použitím `-reference`.<br /><br /> Pokud kód do jednoho modulu odkazuje na vnitřní typy v jiném modulu, musí být oba moduly začleněny do manifestu sestavení s použitím `-reference`.<br /><br /> [- Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) možnost Importuje metadata z modulu.|  
|`-target:winexe`|Způsobí, že kompilátor vytvoří spustitelný soubor aplikace založené na Windows.<br /><br /> Spustitelný soubor se vytvoří s příponou .exe. Aplikace pro systém Windows je ten, který poskytuje uživatelské rozhraní buď z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd nebo pomocí rozhraní API systému Win32.<br /><br /> Pokud není uvedeno jinak se `-out` možnost, název výstupního souboru přebírá název vstupního souboru, který obsahuje `Sub Main` postup.<br /><br /> Pouze jeden `Sub Main` postup je požadován v souborech zdrojového kódu, které jsou kompilovány do souboru s příponou .exe. V případech, kdy váš kód obsahuje více než jednu třídu, která má `Sub Main` postupu, použijte `-main` – možnost kompilátoru k určení, která třída obsahuje `Sub Main` procedury|  
|`-target:appcontainerexe`|Způsobí, že kompilátor vytvoří spustitelný soubor aplikace založené na Windows, která musí být spuštěn v kontejneru aplikace. Toto nastavení je navržená pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikací.<br /><br /> **Appcontainerexe** nastavení nastaví bit v poli vlastnosti [přenosný spustitelný soubor](/windows/desktop/Debug/pe-format) souboru. Tato verze označuje, že aplikace musí být spuštěn v kontejneru aplikace. Pokud je tento bit nastaven, pokud dojde k chybě `CreateProcess` metoda se pokusí spustit aplikaci mimo kontejner aplikace. Kromě toto bit nastavení **-target: appcontainerexe** je ekvivalentní **-target: winexe**.<br /><br /> Spustitelný soubor se vytvoří s příponou .exe.<br /><br /> Pokud neurčíte jinak pomocí `-out` možnost, název výstupního souboru přebírá název vstupního souboru, který obsahuje `Sub Main` postup.<br /><br /> Pouze jeden `Sub Main` postup je požadován v souborech zdrojového kódu, které jsou kompilovány do souboru s příponou .exe. Pokud váš kód obsahuje více než jednu třídu, která má `Sub Main` postupu, použijte `-main` – možnost kompilátoru k určení, která třída obsahuje `Sub Main` procedury|  
|`-target:winmdobj`|Způsobí, že kompilátor vytvořit pomocný soubor, který lze převést do binárního souboru (.winmd) souboru Windows Runtime. Soubor .winmd mohou být spotřebovány programy JavaScript a C++, kromě programů spravovaného jazyka.<br /><br /> Pomocný soubor se vytvoří s příponou .winmdobj.<br /><br /> Pokud neurčíte jinak pomocí `-out` možnost, název výstupního souboru využívá názvu prvního vstupního souboru. A `Sub Main` postup není povinné.<br /><br /> Soubor .winmdobj je určen pro použití jako vstup pro <xref:Microsoft.Build.Tasks.WinMDExp> exportovat nástroj k vytvoření souboru Windows metadata (WinMD). Soubor WinMD obsahuje příponu .winmd a obsahuje kód z původní knihovny i WinMD definice, které jazyk JavaScript, C++ a použití prostředí Windows Runtime.|  
  
 Pokud nezadáte `-target:module`, `-target` způsobí, že [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] manifest sestavení přidán do výstupního souboru.  
  
 Vytváří každou instanci Vbc.exe, maximálně jednu výstupní soubor. Pokud například zadáte možnost kompilátoru `-out` nebo `-target` více než jednou, posledním blokem procesy, které kompilátor je začíná platit. Informace o všech souborech v kompilaci se přidají do manifestu. Všechny výstupní soubory s výjimkou těch, vytvořené pomocí `-target:module` obsahovat metadata sestavení v manifestu. Použití [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1) zobrazit metadata do výstupního souboru.  
  
 Krátký tvar `-target` je `-t`.  
  
### <a name="to-set--target-in-the-visual-studio-ide"></a>Chcete-li nastavit – cíl v integrovaném vývojovém prostředí sady Visual Studio  
  
1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.   
  
2.  Klikněte na tlačítko **aplikace** kartu.  
  
3.  Upravte hodnotu v **typ aplikace** pole.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `in.vb`, vytváření `in.dll`:  
  
```console
vbc -target:library in.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [– referenční dokumentace (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)  
 [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
