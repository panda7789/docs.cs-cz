---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 4f34f7f4ada3f8d61c9d855eab1b8b073a3d5ed8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Určuje, že vlastnost může být zapsána ale číst.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="rules"></a>Pravidla  
 **Kontext deklarace.** Můžete použít `WriteOnly` jenom na úrovni modulu. To znamená kontext deklarace `WriteOnly` vlastnost musí být třída, struktura nebo modul a nemůže být zdrojový soubor, obor názvů nebo postupu.  
  
 Je možné deklarovat vlastnost jako `WriteOnly`, ale nikoli proměnné.  
  
## <a name="when-to-use-writeonly"></a>Kdy použít WriteOnly  
 Někdy budete chtít kód náročné být schopni nastavit hodnotu, ale není zjistit, co je. Například citlivých dat, jako je sociální číslo registrací nebo heslo, musí být chráněny před přístupem jakékoli součásti, která není nastavena. V těchto případech můžete použít `WriteOnly` vlastnost na hodnotu.  
  
> [!IMPORTANT]
>  Pokud definice a používání `WriteOnly` vlastnost, zvažte následující další ochranná opatření:  
  
-   **Přepsání.** Pokud vlastnost člena třídy, aby ji bylo výchozí [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)a jeho nedeklarujte `Overridable` nebo `MustOverride`. Odvozené třídy zabrání provedení nežádoucí přístup pomocí přepsání.  
  
-   **Úroveň přístupu.** Pokud v jedné nebo více proměnných obsahovat vlastnosti citlivá data, je deklarovat [privátní](../../../visual-basic/language-reference/modifiers/private.md) , aby žádný jiný kód přístup.  
  
-   **Šifrování.** Ukládat všechny citlivá data v šifrované podobě, ne ve formátu prostého textu. Pokud škodlivý kód nějakým způsobem získá přístup k této oblasti paměti, je obtížnější Chcete-li použít data. Šifrování je také užitečné, pokud je potřeba serializovat citlivá data.  
  
-   **Resetování.** Když je ukončovány třídy, struktury nebo modul definování vlastnosti, obnovit důvěrné osobní údaje, výchozí hodnoty nebo na jiné smysl hodnoty. To dává zvláštní ochranu při této oblasti paměti uvolněna pro obecné přístup.  
  
-   **Trvalost.** Pokud ho se můžete vyhnout se nezachovají citlivé údaje, například na disku. Navíc Nezapisovat citlivé údaje do schránky.  
  
 `WriteOnly` Modifikátor můžete v tomto kontextu použít:  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
