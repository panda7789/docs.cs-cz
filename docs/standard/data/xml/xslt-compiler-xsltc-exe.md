---
title: Kompilátoru XSLT (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aef49f70f3a60151aa053a1a94a06bc71401531e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xslt-compiler-xsltcexe"></a>Kompilátoru XSLT (xsltc.exe)
Kompilátor XSLT (xsltc.exe) kompiluje XSLT šablony stylů a generuje sestavení. Kompilované šablony stylů mohou být předány pak přímo do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metoda. Podepsaná sestavení s xsltc.exe nelze vygenerovat.  
  
 Nástroj xsltc.exe je součástí sady Visual Studio. Další informace najdete v tématu [Visual Studio stáhne](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a>Argument  
  
|Argument|Popis|  
|--------------|-----------------|  
|`sourceFile`|Určuje název šablony stylů. Šablony stylů musí být místní soubor nebo se nachází na intranetu.|  
  
## <a name="options"></a>Možnosti  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/c[lass]:``name`|Určuje název třídy pro následující šablony stylů. Může být plně kvalifikovaný název třídy.<br /><br /> Název třídy výchozí název šablony stylů. Například pokud customers.xsl list stylu zkompilován, výchozí název třídy je zákazníků.|  
|`/debug[`+&#124;-`]`|Určuje, jestli se má generovat ladicí informace.<br /><br /> Určení `+` nebo `/debug`, způsobí, že kompilátor generovat ladicí informace a umístí jej do souboru databáze (PDB) programu. Je název vygenerovaný soubor PDB `assemblyName`pdb.<br /><br /> Určení `-`, který je v platnosti, pokud nezadáte `/debug`, způsobí, že žádné informace o ladění, který se má vytvořit. Generuje se prodejní sestavení. **Poznámka:** kompilace v režimu ladění může výrazně ovlivnit výkon XSLT.|  
|`/help`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`/nologo`|Potlačí zpráva o autorských právech kompilátoru ze zobrazení.|  
|`/platform:``string`|Určuje platformy, které lze spustit sestavení. Následující text popisuje platformy platné hodnoty:<br /><br /> `x86` zkompiluje vaše sestavení ke spuštění 32-bit, kompatibilní s x86 common language runtime<br /><br /> `x64` zkompiluje vaše sestavení pro modul common language runtime 64-bit spustit na počítači, který podporuje AMD64 nebo EM64T sada instrukcí.<br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] zkompiluje vaše sestavení pro modul common language runtime 64-bit spustit na počítači, který má [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] procesoru.<br /><br /> `anycpu` Zkompiluje vaše sestavení pro spouštěn na libovolné platformě. Toto nastavení je výchozí.|  
|`/out:``assemblyName`|Určuje název sestavení, které je výstup. Pokud jsou k dispozici více šablon stylů, výchozí název sestavení název hlavní šablony stylů nebo první šablony stylů.<br /><br /> Pokud list stylu obsahuje skripty, skripty se uloží do samostatné sestavení. Z názvu hlavní sestavení se generují názvy sestavení skriptu. Například pokud jste zadali CustOrders.dll pro název sestavení, první sestavení skriptu název CustOrders_Script1.dll.|  
|`/settings:``document+-, script+-, DTD+-,`|Určuje, jestli se má povolit `document()` funkce, skript XSLT nebo dokumentu zadejte definice (DTD) v šabloně stylů.<br /><br /> Zakáže podporu pro DTD, použije se výchozí chování `document()` funkce a skriptování.|  
|`@``file`|Umožňuje zadat soubor, který obsahuje možnosti kompilátoru.|  
|`?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 XSLT řešení se může skládat z více modulů list stylu. Nástroj xsltc.exe generuje sestavení ze šablony stylů. Sestavení může být předána do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metoda. To může pomoct snížit náklady na výkon v některých scénářích nasazení XSLT.  
  
> [!NOTE]
>  Navíc musí zahrnovat kompilované sestavení jako odkaz v aplikaci.  
  
 Nástroj xsltc.exe nelze ověřit třídu (`/class:``name`) nebo sestavení (`/out:``assemblyName`) názvy. Chyby jsou vyvolané modul common language runtime, pokud se názvy nejsou platné.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz zkompiluje šablony stylů a vytvoří sestavení s názvem booksort.dll.  
  
```  
xsltc booksort.xsl  
```  
  
 Následující příkaz zkompiluje šablony stylů a vytvoří sestavení a souboru PDB, který je pojmenován booksort.dll a booksort.pdb v uvedeném pořadí.  
  
```  
xsltc booksort.xsl /debug  
```  
  
 Následující příkaz zkompiluje šablony stylů, která obsahuje msxsl:script element a vytvoří dvě sestavení s názvem calc.dll a calc_Script1.dll.  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 Následující příkaz umožňuje podporu specifikace DTD zpracování a skript a vytvoří dvě sestavení s názvem myTest.dll a myTest_Script1.dll.  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 Následující příkaz zkompiluje dva moduly list stylu a vytvoří jednoho sestavení s názvem booksort.dll.  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [Postup: Provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
 [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
