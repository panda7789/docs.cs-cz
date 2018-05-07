---
title: Neplatný vzor řetězce
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 4905f74683989d8e1a2b041a8af4af4d7432ffab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="invalid-pattern-string"></a>Neplatný vzor řetězce
Vzor řetězec zadaný v poli `Like` operace hledání je neplatný.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte platné znaky pro seznam výrazů.  
  
2.  V rozsahu vzor, zajistěte, aby byl znak spuštění rozsah menší než koncový rozsah znak, jako v `[a-z]`.  
  
3.  V rozsahu vzor, ujistěte se, že nejsou k dispozici více pomlčky vedle sebe, jako v `[a--z]`.  
  
4.  Ukončení vzor oblastí s pravá závorka.  
  
## <a name="see-also"></a>Viz také  
 [Operátor Like](../../visual-basic/language-reference/operators/like-operator.md)
