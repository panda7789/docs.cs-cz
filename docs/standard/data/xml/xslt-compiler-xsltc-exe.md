---
title: XSLT Compiler (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 729e6caa36ed8c2f6e77153f8d8ae356513b0603
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956984"
---
# <a name="xslt-compiler-xsltcexe"></a>XSLT Compiler (xsltc.exe)
Kompilátor XSLT (xsltc. exe) kompiluje šablony stylů XSLT a generuje sestavení. Kompilovaná šablona stylů může být předána přímo do metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>. Nelze generovat podepsaná sestavení pomocí xsltc. exe.  
  
 Nástroj xsltc. exe je součástí sady Visual Studio. Další informace najdete v tématu [soubory ke stažení pro Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a>Argument  
  
|Argument|Popis|  
|--------------|-----------------|  
|`sourceFile`|Určuje název předlohy se styly. Šablona stylů musí být místní soubor nebo se nachází na intranetu.|  
  
## <a name="options"></a>Možnosti  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/c[lass]:` `name`|Určuje název třídy pro následující šablonu stylů. Název třídy může být plně kvalifikovaný.<br /><br /> Název třídy je ve výchozím nastavení název předlohy se styly. Například pokud je tabulka stylů Customers. XSL je kompilována, výchozí název třídy je Customers.|  
|`/debug[`+&#124;-`]`|Určuje, zda se mají generovat ladicí informace.<br /><br /> Určení `+` nebo `/debug`způsobí, že kompilátor vygeneruje ladicí informace a umístí je do souboru databáze programu (PDB). Název generovaného souboru PDB je `assemblyName`. pdb.<br /><br /> Určení `-`, což platí v případě, že neurčíte `/debug`, nevytvoří žádné informace o ladění. Vygeneruje se maloobchodní sestavení. **Poznámka:**  Kompilace v režimu ladění může významně ovlivnit výkon XSLT.|  
|`/help`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`/nologo`|Potlačí zobrazení zprávy o autorských právech kompilátoru.|  
|`/platform:` `string`|Určuje platformy, na kterých lze spustit sestavení. Následující popis obsahuje platné hodnoty platformy:<br /><br /> `x86` zkompiluje sestavení tak, aby běželo 32 modul CLR (Common Language Runtime) kompatibilním s platformou x86.<br /><br /> `x64` zkompiluje vaše sestavení tak, aby bylo spuštěno pomocí 64 modulu CLR (Common Language Runtime) v počítači, který podporuje instrukční sady AMD64 nebo EM64T.<br /><br /> Procesory Itanium zkompiluje vaše sestavení tak, aby bylo spuštěno pomocí 64 modulu CLR (Common Language Runtime) v počítači, který má procesor s procesorem Itanium.<br /><br /> `anycpu` zkompiluje vaše sestavení tak, aby běželo na libovolné platformě. Toto nastavení je výchozí.|  
|`/out:` `assemblyName`|Určuje název sestavení, které je výstupem. Název sestavení je výchozím názvem pro hlavní šablonu stylů nebo první šablonu stylů, pokud je k dispozici více šablon stylů.<br /><br /> Pokud šablona stylů obsahuje skripty, skripty jsou uloženy do samostatného sestavení. Názvy sestavení skriptu jsou generovány z hlavního názvu sestavení. Například pokud jste pro název sestavení zadali CustOrders. dll, první sestavení skriptu má název CustOrders_Script1. dll.|  
|`/settings:` `document+-, script+-, DTD+-,`|Určuje, zda mají být v šabloně stylů povoleny funkce `document()`, skript XSLT nebo definice typu dokumentu (DTD).<br /><br /> Výchozí chování zakáže podporu DTD, funkce `document()` a skriptování.|  
|`@` `file`|Umožňuje zadat soubor, který obsahuje možnosti kompilátoru.|  
|`?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Řešení XSLT se mohou skládat z několika modulů šablon stylů. Nástroj xsltc. exe generuje sestavení ze šablon stylů. Sestavení lze následně předat do metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>. To může přispět ke snížení nákladů na výkon v některých scénářích nasazení XSLT.  
  
> [!NOTE]
> Také je nutné zahrnout zkompilované sestavení jako odkaz do aplikace.  
  
 Nástroj xsltc. exe neověřuje názvy tříd (`/class:`*Name*) ani sestavení (`/out:`*AssemblyName*). Pokud názvy nejsou platné, jsou chyby vyvolány modulem CLR (Common Language Runtime).  
  
## <a name="examples"></a>Příklady  
 Následující příkaz zkompiluje šablonu stylů a vytvoří sestavení s názvem booksort. dll.  
  
```console  
xsltc booksort.xsl  
```  
  
 Následující příkaz zkompiluje šablonu stylů a vytvoří sestavení a soubor PDB s názvem booksort. dll a booksort. pdb v uvedeném pořadí.  
  
```console  
xsltc booksort.xsl /debug  
```  
  
 Následující příkaz zkompiluje šablonu stylů obsahující element msxsl: Script a vytvoří dvě sestavení s názvem Calc. dll a calc_Script1. dll.  
  
```console  
xsltc /settings:script+ calc.xsl  
```  
  
 Následující příkaz umožňuje zpracování a podporu skriptu DTD a vytváří dvě sestavení s názvem myTest. dll a myTest_Script1. dll.  
  
```console  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 Následující příkaz zkompiluje dva moduly šablon stylů a vytvoří jedno sestavení s názvem booksort. dll.  
  
```console  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [Postup: Provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
