---
title: Rozdíly mezi stínováním a přepsáním
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: 8d1ebdcd0a23dff69a7acca22268c03e30ec06d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345420"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Rozdíly mezi stínováním a přepsáním (Visual Basic)
Při definování třídy, která dědí ze základní třídy, někdy je vhodné znovu definovat jeden nebo více elementů základní třídy v odvozené třídě. Pro tento účel jsou k dispozici stíny a přepsání.  
  
## <a name="comparison"></a>Porovnání  
 Stíny a přepsání se používají, když odvozená třída dědí ze základní třídy a obě předefinování jednoho deklarovaného elementu s jiným. Existují však významné rozdíly mezi těmito dvěma.  
  
 V následující tabulce je porovnáváno stínování s přepsáním.  
  
||||  
|---|---|---|  
|Bod porovnání|Stínování|Přitom|  
|Účel|Chrání před následnou úpravou základní třídy, která zavádí člena, který jste už definovali v odvozené třídě.|Dosahuje polymorfismu pomocí definování jiné implementace procedury nebo vlastnosti se stejnou volající sekvencí<sup>1</sup> .|  
|Předefinovaný element|Jakýkoli deklarovaný typ elementu|Pouze proceduru (`Function`, `Sub`nebo `Operator`) nebo vlastnost|  
|Předefinování elementu|Jakýkoli deklarovaný typ elementu|Pouze procedura nebo vlastnost se stejnou volající sekvencí<sup>1</sup>|  
|Úroveň přístupu elementu pro definování|Jakákoli úroveň přístupu|Nejde změnit úroveň přístupu přepsaného elementu.|  
|Čitelnost a zapisovatelnosti předefinování elementu|Libovolná kombinace|Nejde změnit čitelnost nebo zapisovatelnosti přepsané vlastnosti.|  
|Kontrola nad předefinováním|Element základní třídy nemůže vyhovět nebo zakázat stíny.|Element základní třídy může určovat `MustOverride`, `NotOverridable`nebo `Overridable`|  
|Použití klíčového slova|`Shadows` doporučené v odvozené třídě; `Shadows` předpokládaná, pokud není zadána hodnota `Shadows` ani `Overrides`<sup>2</sup>|`Overridable` nebo `MustOverride` vyžadovány v základní třídě; `Overrides` vyžadován v odvozené třídě|  
|Dědičnost předefinování elementu pomocí tříd odvozených z odvozené třídy|Stínový element zděděný dalšími odvozenými třídami; stínovaná element je stále skrytý<sup>3</sup>|Přepsání elementu zděděného dalšími odvozenými třídami; přepsání elementu je dál přepsáno.|  
  
 <sup>1</sup> *sekvence volání* se skládá z typu elementu (`Function`, `Sub`, `Operator`nebo `Property`), název, seznam parametrů a návratový typ. Nelze přepsat proceduru s vlastností nebo jiným způsobem kolem. Jeden druh procedury (`Function`, `Sub`nebo `Operator`) nelze přepsat jiným typem.  
  
 <sup>2</sup> Pokud nezadáte buď `Shadows` nebo `Overrides`, kompilátor vydá zprávu s upozorněním, která vám pomůžete zajistit, jaký druh předefinování chcete použít. Pokud upozornění ignorujete, použije se stínový mechanismus.  
  
 <sup>3</sup> Pokud je stínový element nepřístupný v další odvozené třídě, není stíning děděn. Například pokud deklarujete stínový prvek jako `Private`, třída odvozená z odvozené třídy zdědí původní prvek namísto stínového elementu.  
  
## <a name="guidelines"></a>Pokyny  
 Přepsání se obvykle používá v následujících případech:  
  
- Definujete polymorfní odvozené třídy.  
  
- Chcete, aby zabezpečení s kompilátorem vynutilo stejný typ prvku a volací sekvenci.  
  
 Stínování se běžně používá v následujících případech:  
  
- Očekáváte, že vaše základní třída může být upravena a definovat element pomocí stejného názvu jako váš.  
  
- Chcete mít volnost v měně změny typu prvku nebo sekvence volání.  
  
## <a name="see-also"></a>Viz také:

- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Stínování v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Postupy: Skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Postupy: Přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
