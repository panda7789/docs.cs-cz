---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dab9115c31e538bd28583b9f0591ae0c9611e2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Privátní](../../../visual-basic/language-reference/modifiers/private.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
