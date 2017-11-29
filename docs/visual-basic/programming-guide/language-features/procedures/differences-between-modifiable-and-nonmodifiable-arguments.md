---
title: "Rozdíly mezi upravitelnými a neupravitelnými argumenty (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab108d064f5c6740f80328a9b6db4785334550ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Rozdíly mezi upravitelnými a neupravitelnými argumenty (Visual Basic)
Při volání procedury, obvykle předání jeden nebo více argumentů do ní. Každý argument odpovídá základní programovací element. Základní elementy a argumenty sami může být upravitelnými a neupravitelnými.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Upravitelnými a Neupravitelnými elementy  
 Programovací element může být buď *upravitelnými element*, která může mít jeho hodnota změněna, nebo *neupravitelnými element*, který má pevnou hodnotu, po vytvoření.  
  
 Následující tabulka uvádí upravitelnými a neupravitelnými elementům programování.  
  
|Upravitelnými elementy|Neupravitelnými elementy|  
|-------------------------|----------------------------|  
|Lokální proměnné (deklarované uvnitř procedury), včetně objektové proměnné, s výjimkou jen pro čtení|Proměnné jen pro čtení, polí a vlastností|  
|Pole (členské proměnné modulů, třídy a struktury), s výjimkou jen pro čtení|Konstanty a literály|  
|Vlastnosti, s výjimkou jen pro čtení|Členové výčtu|  
|Elementy pole|Výrazy (i když jsou jejich elementů upravitelnými)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Upravitelnými a Neupravitelnými argumenty  
 A *upravitelnými argument* je jedním s upravitelnými základní elementem. Volání kódu můžete uložit novou hodnotu kdykoli, a Pokud předáte argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), kód v postupu můžete také upravit základní elementu v kódu volání.  
  
 A *neupravitelnými argument* má neupravitelnými základní element nebo je předán [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Postup nelze upravit základní element v kód volání, i když je upravitelnými element. Pokud je element neupravitelnými, nelze jej upravovat volání samotný kód.  
  
 Volané procedury může změnit jeho místní kopii neupravitelnými argument, ale tato změna nemá vliv na základní elementu v kódu volání.  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Postupy: předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Předávání argumentů podle hodnoty a podle Reference](./passing-arguments-by-value-and-by-reference.md)  
 [Rozdíly mezi předáním argumentu podle hodnoty a podle Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Postupy: ochrana argumentu procedury proti změnám hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Postupy: vynucení předání hodnotou argumentu](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
