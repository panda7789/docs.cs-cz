---
title: Nástroj XML Serializer Generator Tool (Sgen.exe)
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: bc1a0abaeef9a9244aa83941e590063c7ef167d1
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588366"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>Nástroj XML Serializer Generator Tool (Sgen.exe)

Generátor serializátor XML vytvoří sestavení serializace XML pro typy v zadaném sestavení. Sestavení serializace zlepšuje výkon <xref:System.Xml.Serialization.XmlSerializer> při spuštění při serializaci nebo deserializaci objektů zadaných typů.
  
## <a name="syntax"></a>Syntaxe

Spusťte nástroj z příkazového řádku.
  
```console  
sgen [options]  
```
  
> [!TIP]
> Aby .NET Framework nástroje správně fungovaly, musíte správně nastavit proměnné `Path`prostředí `Include`, a `Lib` . Nastavte tyto proměnné prostředí spuštěním SDKVars. bat, který je umístěný v adresáři \<SDK> \v2.0\Bin Directory. SDKVars.bat je třeba spustit v každém příkazovém prostředí.
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/a\[sestavení\]:**_filename_|Generuje kód serializace pro všechny typy obsažené v sestavení nebo spustitelný soubor určený parametrem *filename*. Lze zadat pouze jeden název souboru. Je-li tento argument se opakuje, se používá poslední název souboru.|  
|**/c\[ompiler\]:**_Možnosti_|Určuje možnosti, které mají být předána do kompilátor jazyka C#. Všechny možnosti CSc. exe jsou podporovány, protože jsou předány kompilátoru. To lze použít k určení, že by měl být podepsáno sestavení a k určení souboru s klíčem.|  
|**/d\[ebug\]**|Generuje obrázek, který lze použít se ladicí program.|  
|**/f\[Orce\]**|Vynutí přepsání existující sestavení se stejným názvem. Výchozí hodnota je **false**.|  
|**/Help nebo/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/k\[achovat\]**|Potlačí odstranění vytvořených zdrojových souborů a jiné dočasné soubory, poté, co byl zkompilován sestavení serializace. To lze použít k určení, zda tento nástroj je generování kódu serializace pro určitý typ.|  
|**/n\[ologo\]**|Potlačí zobrazování úvodní nápis společnosti Microsoft.|  
|**/o\[UT\]:**_path_|Určuje adresář, do kterého chcete uložit vygenerované sestavení. **Poznámka:**  Název generovaného sestavení se skládá z názvu vstupního sestavení plus "xmlSerializers. dll".|  
|**/p\[roxytypes\]**|Generuje kód serializace pouze pro typy XML webové služby proxy serveru.|  
|**/r\[eference\]:**_assemblyfiles_|Určuje sestavení, která je odkazováno dle typy vyžadujících serializace XML. Je možné zadat více souborů sestavení, oddělených čárkami.|  
|**/s\[ilent\]**|Potlačí zobrazování zpráv o úspěšném dokončení.|  
|**/t\[typ\]:**_typ_|Generuje kód serializace pouze u zadaného typu.|  
|**/v\[erbose\]**|Zobrazí podrobné informace pro ladění. Zobrazí seznam typů z cílového sestavení, které nelze serializovat, s <xref:System.Xml.Serialization.XmlSerializer>.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud není použit generátor serializátor XML, <xref:System.Xml.Serialization.XmlSerializer> generuje serializace kódu a sestavení serializace pro každý typ při každém spuštění aplikace. Chcete-li zlepšit výkon při spuštění serializace XML, použijte nástroj Sgen. exe ke generování těchto sestavení předem. Tyto sestavení lze nasadit poté s aplikací.  
  
 Generátor serializátor XML můžete také zvýšit výkon klienty, kteří používají ke komunikaci se servery, protože proces serializace nesmí být účtovány výkonu, poté klikněte na tlačítko při prvním načtení typ proxy XML webové služby.  
  
 Tyto vygenerované sestavení nelze použít na straně serveru webové služby. Tento nástroj je jen pro scénáře ruční serializace a klienti webové služby.  
  
 Pokud sestavení obsahující typ k serializaci název MyType.dll, pak sestavení přidružené serializace bude pojmenován MyType.XmlSerializers.dll.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vytvoří sestavení s názvem Data.XmlSerializers.dll pro serializaci všechny typy, které jsou obsaženy v sestavení s názvem Data.dll.  
  
```console  
sgen Data.dll
```  
  
 Data.XmlSerializers.dll sestavení lze odkazovat z kódu, který potřebuje k serializaci a deserializaci typy v Data.dll.  
  
## <a name="see-also"></a>Viz také

- [Nástroje](../../../docs/framework/tools/index.md)
- [Výzvy příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
