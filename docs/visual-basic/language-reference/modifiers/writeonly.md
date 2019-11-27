---
title: WriteOnly
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
ms.openlocfilehash: 847617ea6534089857a759fbea3bb16a3a5a36a1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344193"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Určuje, že vlastnost může být zapsána, ale nebude přečtena.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="rules"></a>Pravidla  
 **Kontext deklarace** `WriteOnly` můžete použít jenom na úrovni modulu. To znamená, že kontext deklarace pro vlastnost `WriteOnly` musí být třída, struktura nebo modul a nemůže se jednat o zdrojový soubor, obor názvů nebo proceduru.  
  
 Vlastnost můžete deklarovat jako `WriteOnly`, ale ne proměnnou.  
  
## <a name="when-to-use-writeonly"></a>Kdy použít WriteOnly  
 Někdy budete chtít, aby kód byl schopný nastavit hodnotu, ale nezjistit, co je. Například citlivá data, jako je číslo rodného čísla nebo heslo, musí být chráněna před přístupem libovolné součásti, která ji nestavila. V těchto případech můžete použít vlastnost `WriteOnly` k nastavení hodnoty.  
  
> [!IMPORTANT]
> Při definování a použití vlastnosti `WriteOnly` Vezměte v úvahu následující dodatečná ochranná opatření:  
  
- **Přitom.** Pokud je vlastnost členem třídy, umožněte jí, aby jí bylo možné [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)a Nedeklarujte ji `Overridable` nebo `MustOverride`. Tím zabráníte odvozeným třídám v provedení nežádoucího přístupu prostřednictvím přepsání.  
  
- **Úroveň přístupu.** Pokud podržíte citlivá data vlastnosti v jedné nebo více proměnných, deklarujte je jako [soukromá](../../../visual-basic/language-reference/modifiers/private.md) , aby k nim nikdo nepřístupoval žádný jiný kód.  
  
- **Šifr.** Ukládat všechna citlivá data v zašifrované podobě, nikoli v prostém textu. Pokud škodlivý kód nějakým způsobem získá přístup k této oblasti paměti, je obtížnější využít data. Šifrování je užitečné také v případě, že je nutné serializovat citlivá data.  
  
- **Resetování.** Když je ukončena třída, struktura nebo modul definující vlastnost, resetujte citlivé údaje na výchozí hodnoty nebo jiné nevýznamné hodnoty. To poskytuje dodatečnou ochranu, pokud je tato oblast paměti uvolněna pro obecný přístup.  
  
- **Dočasné.** Neuchovávat žádná citlivá data, například na disku, pokud se k tomu můžete vyhnout. Nepište také žádná citlivá data do schránky.  
  
 V tomto kontextu lze použít modifikátor `WriteOnly`:  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
