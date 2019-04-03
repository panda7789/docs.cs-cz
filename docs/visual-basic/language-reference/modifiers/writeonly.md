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
ms.openlocfilehash: 1b8de27e872914ba59d73126d2a9a7c42609165e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829020"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Určuje, že vlastnost může zapisovat, ale nedá se číst.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="rules"></a>pravidla  
 **Místní deklarace.** Můžete použít `WriteOnly` pouze na úrovni modulu. To znamená, že deklarace kontext `WriteOnly` vlastnost musí být třída, struktura nebo modulu a nemůže být zdrojový soubor, obor názvů nebo proceduru.  
  
 Je možné deklarovat vlastnost jako `WriteOnly`, ale není proměnná.  
  
## <a name="when-to-use-writeonly"></a>Kdy použít jen pro zápis  
 Někdy chcete být schopni nastavit hodnotu, ale ne zjistit, co to je časově náročný kód. Například citlivá data, jako jsou sociální registrační číslo nebo heslo, musí být chráněny před přístup jakékoli součásti, která nebyla nastavena. V těchto případech můžete použít `WriteOnly` vlastnosti chcete nastavit hodnotu.  
  
> [!IMPORTANT]
>  Při definování a použití `WriteOnly` vlastnost, vezměte v úvahu následující další ochranná opatření:  
  
-   **Přepsání.** Pokud je vlastnost člena třídy, mohla ve výchozím nastavení [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)a ne jeho deklarace `Overridable` nebo `MustOverride`. To brání odvozené třídy v provádění nežádoucích přístup pomocí přepsání.  
  
-   **Úroveň přístupu.** Pokud jste v jedné nebo více proměnných citlivých dat vlastnost, je deklarovat [privátní](../../../visual-basic/language-reference/modifiers/private.md) tak, aby k nim může přistupovat žádný kód.  
  
-   **Šifrování.** Store všechna citlivá data v zašifrované podobě, nikoli ve formátu prostého textu. Pokud škodlivý kód nějakým způsobem získá přístup k této oblasti paměti, je obtížnější, chcete-li využívají data. Šifrování je také užitečné, pokud je nutné k serializaci citlivá data.  
  
-   **Resetuje se.** Když se ukončuje třídy, struktury nebo modul definující vlastnosti, obnovit citlivých dat na výchozí hodnoty nebo na další význam hodnoty. Díky tomu ochrany při této oblasti paměti je uvolněna obecného přístupu.  
  
-   **Trvalost.** Pokud ho se můžete vyhnout nezůstanou zachována citlivých dat, třeba na disku. Citlivé údaje taky nezapisujte do schránky.  
  
 `WriteOnly` Modifikátor lze použít v tomto kontextu:  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
