---
title: Předávání argumentů podle hodnoty a odkazu (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f10e0e582e060c1305a9c0fe922620cb4da2c215
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Předávání argumentů podle hodnoty a odkazu (Visual Basic)
V jazyce Visual Basic, můžete předat argument proceduře *hodnotou* nebo *odkazem*. To se označuje jako *předávání mechanismus*, a určuje, zda postupu můžete upravit programovací element základní argument ve volání kódu. Deklarace procedury určuje předávání mechanismus pro každý parametr zadáním [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo.  
  
## <a name="distinctions"></a>Rozlišení  
 Při předávání argumentu procedury, nezapomeňte několik různých rozdíly, které spolupracují mezi sebou:  
  
-   Jestli je základní programovací element upravitelnými a neupravitelnými  
  
-   Jestli je samotného argumentu upravitelnými a neupravitelnými  
  
-   Jestli argument je předávána hodnotou nebo odkazem  
  
-   Jestli datový typ argumentu je hodnota typu nebo typu odkazu.  
  
 Další informace najdete v tématu [rozdíly mezi upravitelnými a Neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md) a [rozdíly mezi předáním argumentu podle hodnoty a podle Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Volba předávání mechanismus  
 Měli byste vybrat mechanismus předávání pečlivě pro každý argument.  
  
-   **Ochrana**. Ve výběru mezi dvěma předávání mechanismy, je nejdůležitější kritérium ohrožení volání proměnné, které chcete změnit. Výhodou předáním argumentu `ByRef` je, že postup můžete vrátit hodnotu volání kódu pomocí tohoto argumentu. Výhodou předáním argumentu `ByVal` je chrání proměnné před změnou procedurou.  
  
-   **Výkon**. I když tento mechanismus předávání mohou ovlivnit výkon kódu, je obvykle zanedbatelný rozdíl. Jedinou výjimkou je typu hodnota předaná `ByVal`. V takovém případě jazyka Visual Basic zkopíruje obsah celého datového argumentu. Proto na typ velké hodnoty, které by bylo třeba strukturou, může být efektivnější předáváme `ByRef`.  
  
     Pro odkazové typy pouze má ukazatel na data je zkopírovaný (čtyři bajtů na platformách 32-bit, osm bajtů na 64bitových platformách). Proto můžete předat argumenty typu `String` nebo `Object` hodnotou bez poškozování výkonu.  
  
## <a name="determination-of-the-passing-mechanism"></a>Stanovení mechanismus předávání  
 Deklarace procedury určuje předávání mechanismus pro jednotlivé parametry. Volání kódu nejde přepsat `ByVal` mechanismus.  
  
 Pokud je parametr deklarovat s `ByRef`, volající kód můžete vynutit mechanismus `ByVal` uzavřením argument názvu v závorkách ve volání. Další informace najdete v tématu [postupy: vynucení předání hodnotou argumentu](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 Ve výchozím nastavení v jazyce Visual Basic se předání argumentů hodnotou.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Když k předání argumentu podle hodnoty  
  
-   Pokud volání kód element základní argument je neupravitelnými, deklarovat s odpovídajícím parametrem [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Žádný kód můžete změnit hodnotu neupravitelnými elementu.  
  
-   Pokud je základní element upravitelnými, ale nechcete, aby postup nebudete moct změnit jeho hodnotu, deklarovat parametr `ByVal`. Pouze volací kód můžete změnit hodnotu upravitelnými elementu předaná hodnota.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Když k předání argumentu podle Reference  
  
-   Pokud má procedura originální potřeba změnit základní elementu v kódu volání, deklarovat s odpovídajícím parametrem [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
-   Pokud správné spuštění kódu závisí na procesu Změna základní elementu v kódu volání, deklarovat parametr `ByRef`. Pokud předáte hodnotu, nebo pokud volací kód přepíše `ByRef` předávání mechanismus uzavřením argument do závorek, volání procedury může vést k neočekávaným výsledkům.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ilustruje, kdy předání argumentů hodnotou a kdy se mají předat je odkazem. Postup `Calculate` má oba `ByVal` a `ByRef` parametr. Zadané úrokové sazby, `rate`a součet hodnot peníze, `debt`, úloha procedury je k výpočtu nové hodnoty pro `debt` který je výsledkem použití úrokové sazby na původní hodnotu `debt`. Protože `debt` je `ByRef` parametr nové celkem se odrazí v hodnota argumentu v volací kód, který odpovídá `debt`. Parametr `rate` je `ByVal` parametr protože `Calculate` neměli měnit jeho hodnotu.  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Postupy: Ochrana argumentu procedury před změnami hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Postupy: Vynucení předání argumentu podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
