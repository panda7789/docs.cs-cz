---
title: XSLT Compiler (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8480e2d6817d0367e89542c0e6c89cd26183dd5e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774897"
---
# <a name="xslt-compiler-xsltcexe"></a>XSLT Compiler (xsltc.exe)
Kompilátor XSLT (xsltc.exe) zkompiluje šablon stylů XSLT a generuje sestavení. Zkompilované šablony stylů je pak možné předat přímo do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody. Podepsaná sestavení s xsltc.exe nelze generovat.  
  
 Nástroj xsltc.exe je součástí sady Visual Studio. Další informace najdete v tématu [stahování sady Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a>Argument  
  
|Argument|Popis|  
|--------------|-----------------|  
|`sourceFile`|Určuje název šablony stylů. Šablona stylů musí být místní soubor nebo umístěného v intranetu.|  
  
## <a name="options"></a>Možnosti  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/c[lass]:``name`|Určuje název třídy pro následující šablony stylů. Může být plně kvalifikovaný název třídy.<br /><br /> Výchozí název třídy na název šablony stylů. Například pokud je kompilován customers.xsl list stylu, výchozí název třídy je zákazníkům.|  
|`/debug[`+&#124;-`]`|Určuje, jestli se má generovat ladicí informace.<br /><br /> Určení `+` nebo `/debug`, způsobí, že kompilátor generovat ladicí informace a vložit ho do souboru databáze (PDB) programu. Název generovaného souboru PDB je `assemblyName`.pdb.<br /><br /> Určení `-`, který je v platnosti, pokud nezadáte `/debug`, způsobí, že žádné informace o ladění, který se má vytvořit. Maloobchodní sestavení je generováno. **Poznámka:**  Kompilace v režimu ladění může ovlivnit výkon XSLT pouze výrazně.|  
|`/help`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`/nologo`|Potlačí zprávu o autorských právech kompilátoru ze zobrazení.|  
|`/platform:``string`|Určuje sestavení můžete spustit na platformách. Následující část popisuje hodnoty platné platformy:<br /><br /> `x86` kompiluje sestavení ke spuštění v 32bitové, které je kompatibilní x86 common language runtime<br /><br /> `x64` kompiluje sestavení ke spuštění modulem common language runtime 64-bit na počítači, který podporuje AMD64 nebo EM64T instrukční sadu.<br /><br /> Itanium kompiluje sestavení ke spuštění modulem common language runtime 64-bit na počítač s procesorem Itanium.<br /><br /> `anycpu` Kompiluje sestavení pro spouštěn na libovolné platformě. Toto nastavení je výchozí.|  
|`/out:``assemblyName`|Určuje název sestavení, které je výstup. Název sestavení použije výchozí název hlavní šablony stylů nebo první šablony stylů, pokud jsou k dispozici více šablony stylů.<br /><br /> Pokud šablona stylů obsahuje skripty, skripty se uloží do samostatného sestavení. Názvy sestavení skriptu se generují z názvu hlavní sestavení. Například pokud jste zadali pro název vašeho sestavení CustOrders.dll, první skript sestavení je pojmenováno CustOrders_Script1.dll.|  
|`/settings:``document+-, script+-, DTD+-,`|Určuje, jestli se má povolit `document()` funkce XSLT skriptu nebo dokumentu typ definice (DTD) v šabloně stylů.<br /><br /> Výchozí chování zakáže podporu pro DTD, `document()` funkce a skriptování.|  
|`@``file`|Umožňuje určit soubor obsahující možnosti kompilátoru.|  
|`?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Řešení XSLT se může skládat z více modulů list stylu. Nástroj xsltc.exe generuje sestavení ze šablony stylů. Sestavení je pak možné předat do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody. To může pomoct snížit náklady na výkon v některých scénářích nasazení XSLT.  
  
> [!NOTE]
>  Je také nutné uvést zkompilovaného sestavení jako odkaz ve vaší aplikaci.  
  
 Nástroj xsltc.exe nelze ověřit třídu (`/class:`*název*) nebo sestavení (`/out:`*assemblyName*) názvy. Chyby jsou vyvolány pomocí modul common language runtime, pokud názvy nejsou platné.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz zkompiluje šablony stylů a vytvoří sestavení s názvem booksort.dll.  
  
```  
xsltc booksort.xsl  
```  
  
 Následující příkaz zkompiluje šablony stylů a vytvoří sestavení a soubor PDB, které jsou pojmenovány booksort.dll a booksort.pdb v uvedeném pořadí.  
  
```  
xsltc booksort.xsl /debug  
```  
  
 Následující příkaz zkompiluje šablony stylů, která obsahuje element msxsl: Script a vytvoří dvě sestavení s názvem calc.dll a calc_Script1.dll.  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 Následující příkaz povolí zpracování a skript podporu specifikace DTD a vytvoří dvě sestavení s názvem myTest.dll a myTest_Script1.dll.  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 Následující příkaz pro kompilaci dvou modulů list stylu a vytvoří jednoho sestavení s názvem booksort.dll.  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [Postupy: Provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
