---
title: Obory názvů a specifikace DTD v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92d7a50d2db25f5e4d32734d550ce2d55a02e3c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="namespaces-and-dtds-in-the-dom"></a>Obory názvů a specifikace DTD v modelu DOM
Podpora complicate obor názvů typu definice (specifikace DTD) dokumentu. Například následující kód XML obsahuje výchozí atributy, která obsahuje dvojtečky jejich názvy.  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 Toto jsou možná řešení, pokud je povolena tato konstrukce:  
  
-   `x:` Je zpracovaná jako Předpona oboru názvů, ale tato předpona musí být možné přeložit pomocí `xmlns:x` deklaraci oboru názvů, který musí někde existovat také ve DTD. Jedná se o chybu mapovat tuto předponu něco jiného v dokumentu instance.  
  
-   `x:` Je považován za předponu oboru názvů, ale tato předpona je vždy přeložit v kontextu instance elementů. To znamená, že předpona, která může ve skutečnosti mapování na jiný obor názvů identifikátory Uniform Resource (Identifier), v závislosti na oboru názvů, ve kterém `item` prvek se zobrazuje. Toto chování je předvídatelnější než zadaná v dřívější odrážka rozlišení, ale má jiné složité následky, protože vyžaduje vyžaduje výchozí atributy.  
  
-   Dvojtečkou se ignoruje, protože je v DTD a název atributu je `x:y`, žádná předpona a žádný identifikátor URI oboru názvů.  
  
-   Dvojtečka v výchozí atribut vyvolá výjimku, informacemi o tom, že použití dvojteček v názvech definici DTD nejsou podporovány. Výsledkem je předvídatelný chování, ale nemůže načíst řadu World Wide Web Consortium (W3C) znamená publikovaný specifikace DTD.  
  
-   Pokud uživatel požádá o ověření DTD, podpora obor názvů pro celý dokument je vypnutý. Díky tomu je možné načíst specifikace DTD W3C a výsledkem je předvídatelný chování.  
  
 Kód XML v rozhraní Microsoft .NET Framework implementuje druhá možnost pro maximální kompatibility W3C.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
