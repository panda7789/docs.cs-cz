---
title: "Nástroje Generátor serializátor XML (Sgen.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 73669fcfd74f9c4948c8ec976ff3271c72f1033a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>Nástroje Generátor serializátor XML (Sgen.exe)
Vytvoří generátor serializátor XML sestavení serializace XML pro typy v zadané sestavení s cílem zlepšit výkon při spuštění <xref:System.Xml.Serialization.XmlSerializer> při serializuje nebo deserializuje objekty zadaného typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sgen [options]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/a**[**ssembly**]**:***filename*|Generuje kód serializace pro všechny typy, které jsou součástí sestavení nebo spustitelný soubor určený podle *filename*. Lze zadat pouze jeden název souboru. Je-li tento argument se opakuje, se používá poslední název souboru.|  
|**/c [ompiler]:** *možnosti*|Určuje možnosti, které mají být předána do kompilátor jazyka C#. Všechny možnosti csc.exe jsou podporovány při předání kompilátoru. To lze použít k určení, že by měl být podepsáno sestavení a k určení souboru s klíčem.|  
|**/d**[**ebug**]|Generuje obrázek, který lze použít se ladicí program.|  
|**/f [orce]**|Vynutí přepsání existující sestavení se stejným názvem. Výchozí hodnota je **false**.|  
|**/ help nebo /?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/k**[**achovat**]|Potlačí odstranění vytvořených zdrojových souborů a jiné dočasné soubory, poté, co byl zkompilován sestavení serializace. To lze použít k určení, zda tento nástroj je generování kódu serializace pro určitý typ.|  
|**/n**[**ologo**]|Potlačí zobrazování úvodní nápis společnosti Microsoft.|  
|**/o**[**ut**]**:***cesta*|Určuje adresář, do kterého chcete uložit vygenerované sestavení. **Poznámka:** název generovaného sestavení se skládá z název vstupní sestavení plus "xmlSerializers.dll".|  
|**/p**[**roxytypes**]|Generuje kód serializace pouze pro typy XML webové služby proxy serveru.|  
|**/r**[**rnovat**]**:***assemblyfiles*|Určuje sestavení, která je odkazováno dle typy vyžadujících serializace XML. Je možné zadat více souborů sestavení, oddělených čárkami.|  
|**/s**[**ilent**]|Potlačí zobrazování zpráv o úspěšném dokončení.|  
|**/t**[**adejte**]**:***typu*|Generuje kód serializace pouze u zadaného typu.|  
|**/v**[**erbose**]|Zobrazí podrobné informace pro ladění. Zobrazí seznam typů z cílového sestavení, které nelze serializovat, s <xref:System.Xml.Serialization.XmlSerializer>.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud není použit generátor serializátor XML, <xref:System.Xml.Serialization.XmlSerializer> generuje serializace kódu a sestavení serializace pro každý typ při každém spuštění aplikace. Chcete-li zlepšit výkon při spuštění serializace XML, použijte nástroj Sgen.exe ke generování těchto sestavení sestavení předem. Tyto sestavení lze nasadit poté s aplikací.  
  
 Generátor serializátor XML můžete také zvýšit výkon klienty, kteří používají ke komunikaci se servery, protože proces serializace nesmí být účtovány výkonu, poté klikněte na tlačítko při prvním načtení typ proxy XML webové služby.  
  
 Tyto vygenerované sestavení nelze použít na straně serveru webové služby. Tento nástroj je jen pro scénáře ruční serializace a klienti webové služby.  
  
 Pokud sestavení obsahující typ k serializaci název MyType.dll, pak sestavení přidružené serializace bude pojmenován MyType.XmlSerializers.dll.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vytvoří sestavení s názvem Data.XmlSerializers.dll pro serializaci všechny typy, které jsou obsaženy v sestavení s názvem Data.dll.  
  
```  
sgen Data.dll   
```  
  
 Data.XmlSerializers.dll sestavení lze odkazovat z kódu, který potřebuje k serializaci a deserializaci typy v Data.dll.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Přehled webové služby XML](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
