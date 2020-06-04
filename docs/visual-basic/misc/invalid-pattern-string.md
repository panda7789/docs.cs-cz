---
title: Neplatný řetězec vzoru
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: aa408f4cecc2a2774cb98cba96cd04a67afcc546
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402210"
---
# <a name="invalid-pattern-string"></a>Neplatný řetězec vzoru
Řetězec vzorku zadaný v `Like` operaci hledání je neplatný.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zkontrolujte platné znaky pro seznam výrazů.  
  
2. V rozsahu vzorku zajistěte, aby byl znak začátku rozsahu menší než znak koncového rozsahu, jako v `[a-z]` .  
  
3. V rozsahu vzorů zajistěte, aby vedle sebe nebyla více spojovníků, jako v `[a--z]` .  
  
4. Ukončit rozsahy vzorů s pravou závorkou  
  
## <a name="see-also"></a>Viz také

- [Like – operátor](../language-reference/operators/like-operator.md)
