---
title: "Neplatný vzor řetězce"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f824a5844d6d2b365358030119826266a4b42ef3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="invalid-pattern-string"></a>Neplatný vzor řetězce
Vzor řetězec zadaný v poli `Like` operace hledání je neplatný.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte platné znaky pro seznam výrazů.  
  
2.  V rozsahu vzor, zajistěte, aby byl znak spuštění rozsah menší než koncový rozsah znak, jako v `[a-z]`.  
  
3.  V rozsahu vzor, ujistěte se, že nejsou k dispozici více pomlčky vedle sebe, jako v `[a--z]`.  
  
4.  Ukončení vzor oblastí s pravá závorka.  
  
## <a name="see-also"></a>Viz také  
 [Like – operátor](../../visual-basic/language-reference/operators/like-operator.md)
