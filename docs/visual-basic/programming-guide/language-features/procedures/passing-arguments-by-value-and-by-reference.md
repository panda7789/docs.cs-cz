---
title: Předávání argumentů podle hodnoty a odkazu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: eb2260c6547d4f1cd7d9c23445ac38ac600e3535
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638870"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Předávání argumentů podle hodnoty a odkazu (Visual Basic)
V jazyce Visual Basic, můžete předat argument procedury *podle hodnoty* nebo *odkazem*. To se označuje jako *předávání mechanismus*, a určí, zda procesu můžete upravit programový element základní argumentu ve volajícím kódu. Deklarace procedury určuje předávání mechanismus pro každý parametr zadáním [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo.  
  
## <a name="distinctions"></a>Rozdíly  
 Při předávání argumentu procedury, mějte na paměti z několika různých rozdíly, které spolu interagují:  
  
- Určuje, zda je základní programovací element upravitelnými a neupravitelnými  
  
- Určuje, zda je samotný argument upravitelnými a neupravitelnými  
  
- Určuje, zda je právě argument předaný hodnotou nebo odkazem.  
  
- Určuje, zda datový typ argumentu je typ hodnoty nebo typ odkazu  
  
 Další informace najdete v tématu [rozdíly mezi upravitelnými a Neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md) a [rozdíly mezi předáním argumentu podle hodnoty a podle Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Možnost předávání mechanismus  
 Měli byste zvolit mechanismus předávání pečlivě pro každý argument.  
  
- **Ochrana**. Při rozhodování mezi dvěma předávání mechanismy, je nejdůležitější kritérium volání proměnné, chcete-li změnit možnost vidět. Výhodou předání argumentu `ByRef` je, že procedura může vrátit hodnotu volajícímu kódu prostřednictvím tohoto argumentu. Výhodou předání argumentu `ByVal` je chrání proměnnou před změnou procedurou.  
  
- **Výkon**. I když mechanismus předávání může ovlivnit výkon kódu, je obvykle zanedbatelný rozdíl. Jedinou výjimkou je typ hodnoty předané `ByVal`. V takovém případě jazyka Visual Basic zkopíruje obsah celého datového argumentu. Proto se pro typ velké hodnoty jako je například struktura, může být efektivnější předat `ByRef`.  
  
     Pro typy odkazů pouze ukazatel na data je zkopírovaný (čtyř bajtů na 32bitových platformách, osm bajtů na 64bitových platformách). Proto můžete předat argumenty typu `String` nebo `Object` podle hodnoty bez poškození výkonu.  
  
## <a name="determination-of-the-passing-mechanism"></a>Stanovení mechanismu pro předávání  
 Deklarace procedury určuje předávání mechanismus pro každý parametr. Volající kód nelze přepsat `ByVal` mechanismus.  
  
 Pokud parametr je deklarována s `ByRef`, volající kód může vynutit mechanismus pro `ByVal` uzavřením název argumentu do závorek při volání metody. Další informace najdete v tématu [jak: Vynucení argumentu být předána podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 Ve výchozím nastavení v jazyce Visual Basic je předání argumentů podle hodnoty.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Když pro předání argumentu podle hodnoty  
  
- Pokud volání prvek kódu základní argument je prvek neupravitelnými, deklarujte odpovídajícího parametru [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Žádný kód může změnit hodnotu neupravitelnými prvku.  
  
- Pokud je základní prvek upravitelná, ale nechcete, aby postupu moct změnit jeho hodnotu, deklarujte parametr `ByVal`. Pouze volající kód může změnit hodnotu prvku upravitelná předán podle hodnoty.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Kdy se mají předat Argument odkazem.  
  
- Pokud má procedura originální potřeba měnit základní prvek ve volajícím kódu, deklarujte odpovídajícího parametru [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
- Pokud správné spuštění kódu závisí na postup změna základního elementu ve volajícím kódu, deklarujte parametr `ByRef`. Pokud předáte podle hodnoty nebo pokud volající kód přepíše `ByRef` předávání mechanismus uzavřením argument v závorkách, volání procedury může vést k neočekávaným výsledkům.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje, kdy se mají předat argumenty podle hodnoty a při předávání pomocí odkazu. Postup `Calculate` jsou obě `ByVal` a `ByRef` parametru. Vzhledem úrokové sazby `rate`a součet peníze, `debt`, úlohou postupu je vypočítat nové hodnoty pro `debt` , který je výsledkem použití úrokové sazby na původní hodnoty `debt`. Protože `debt` je `ByRef` parametr, nové celkem se projeví v hodnotu argumentu ve volajícím kódu, který odpovídá `debt`. Parametr `rate` je `ByVal` parametr protože `Calculate` by neměly měnit jeho hodnotu.  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Postupy: Ochrana argumentu procedury proti změnám hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Postupy: Vynucení argumentu být předána podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
