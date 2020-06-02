---
title: Obory názvů a specifikace DTD v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
ms.openlocfilehash: 748be66c255aa018fb3e1ed541c6e5a92775408c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288781"
---
# <a name="namespaces-and-dtds-in-the-dom"></a>Obory názvů a specifikace DTD v modelu DOM
Definice typu dokumentu (DTD) komplikuje podporu oboru názvů. Například následující kód XML obsahuje výchozí atributy obsahující dvojtečky ve svých názvech.  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 Níže jsou uvedena možná řešení, pokud je tato konstrukce povolená:  
  
- `x:`Je považován za předponu oboru názvů, ale tuto předponu je nutné přeložit pomocí `xmlns:x` deklarace oboru názvů, která musí také existovat někde v DTD. Namapování této předpony na jinou hodnotu v dokumentu instance je chyba.  
  
- `x:`Je považován za předponu oboru názvů, ale tato předpona je vždy vyřešena v kontextu prvků instance. To znamená, že předpona může být ve skutečnosti namapována na různé obory názvů identifikátorů URI (Uniform Resource Identifier), v závislosti na oboru názvů, ve kterém `item` se prvek zobrazí. Toto chování je více předvídatelné než řešení uvedené v předchozí odrážce, ale má jiné složité důsledky, protože vyžaduje, aby byly výchozí atributy vyhodnoceny.  
  
- Dvojtečka se ignoruje, protože je v definici DTD a název atributu je `x:y` , bez předpony a žádného identifikátoru URI oboru názvů.  
  
- Dvojtečka ve výchozím atributu vyvolá výjimku, která říká, že dvojtečky v názvech uvnitř DTD nejsou podporovány. Výsledkem je předvídatelné chování, ale znamená, že nemůžete načíst mnoho publikovaných definic DTD konsorcium World Wide Web (W3C).  
  
- Když uživatel vyžádá ověření DTD, podpora oboru názvů pro celý dokument je vypnuta. Díky tomu je možné načíst specifikace DTD W3C a výsledky v předvídatelném chování.  
  
 XML v Microsoft .NET Framework implementuje druhou možnost maximální kompatibility W3C.  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
