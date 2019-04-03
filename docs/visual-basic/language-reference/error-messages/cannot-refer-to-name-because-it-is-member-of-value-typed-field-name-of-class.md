---
title: Na člena '<name>' nelze odkazovat, protože se jedná o člen pole typu hodnota '<name>' třídy '<classname>', jehož třídou Base je 'System.MarshalByRefObject'.
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: aac190119ced74496c4dd012d200fca6d895ff28
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826766"
---
# <a name="cannot-refer-to-name-because-it-is-a-member-of-the-value-typed-field-name-of-class-classname-which-has-systemmarshalbyrefobject-as-a-base-class"></a>Nemůže odkazovat na "\<název >" protože se jedná o člen pole typu hodnota '\<název > "' třídy\<classname >' obsahující 'System.MarshalByRefObject' jako základní třída
`System.MarshalByRefObject` Třída umožňuje aplikacím, které podporují vzdálený přístup k objektům přes hranice aplikačních domén. Typy musí dědit z `MarshalByRejectObject` třídy, pokud je typ použít přes hranice aplikačních domén. Stav objektu nesmí být zkopírována, protože členové objektu nejsou použitelné mimo doménu aplikace, ve kterém byly vytvořeny.  
  
 **ID chyby:** BC30310  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, abyste měli jistotu, že je člen, který se odkazuje na platný odkaz.  
  
2.  Explicitně kvalifikovat člena s `Me` – klíčové slovo.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.MarshalByRefObject>
- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
