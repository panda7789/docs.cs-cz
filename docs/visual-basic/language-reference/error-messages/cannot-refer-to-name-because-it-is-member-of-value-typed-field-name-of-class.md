---
title: Na člena '<name>' nelze odkazovat, protože se jedná o člen pole typu hodnota '<name>' třídy '<classname>', jehož třídou Base je 'System.MarshalByRefObject'.
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: 78b0a3131b6e77ed257f200523ecebd4dfce3691
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316541"
---
# <a name="cannot-refer-to-name-because-it-is-a-member-of-the-value-typed-field-name-of-class-classname-which-has-systemmarshalbyrefobject-as-a-base-class"></a>Nemůže odkazovat na "\<název >" protože se jedná o člen pole typu hodnota '\<název > "' třídy\<classname >' obsahující 'System.MarshalByRefObject' jako základní třída
`System.MarshalByRefObject` Třída umožňuje aplikacím, které podporují vzdálený přístup k objektům přes hranice aplikačních domén. Typy musí dědit z `MarshalByRejectObject` třídy, pokud je typ použít přes hranice aplikačních domén. Stav objektu nesmí být zkopírována, protože členové objektu nejsou použitelné mimo doménu aplikace, ve kterém byly vytvořeny.  
  
 **ID chyby:** BC30310  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zkontrolujte, abyste měli jistotu, že je člen, který se odkazuje na platný odkaz.  
  
2. Explicitně kvalifikovat člena s `Me` – klíčové slovo.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.MarshalByRefObject>
- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
