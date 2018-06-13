---
title: Seskupení výsledků podle sousedních klíčů
description: Jak seskupení výsledků podle sousedních klíčů.
ms.date: 12/1/2016
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: a8d6ac133932a12154d5b23454065144c7652067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281434"
---
# <a name="group-results-by-contiguous-keys"></a>Seskupení výsledků podle sousedních klíčů

Následující příklad ukazuje, jak k seskupení prvků do bloků, které představují dílčích sekvencí sousedních klíčů. Předpokládejme například, že budete mít k následujícímu pořadí páry klíč hodnota:  
  
|Key|Hodnota|  
|---------|-----------|  
|OBJEKT|Jsme|  
|OBJEKT|Vezměte v úvahu|  
|OBJEKT|který|  
|B|LINQ|  
|C|is|  
|OBJEKT|Vážně|  
|B|Cool|  
|B|!|  
  
 Tyto skupiny se vytvoří v tomto pořadí:  
  
1.  Myslíme, který  
  
2.  LINQ  
  
3.  is  
  
4.  Vážně  
  
5.  nástrojů!  
  
 Řešení je implementovaný jako metody rozšíření, který je bezpečný pro přístup z více vláken a která vrací své výsledky streamování způsobem. Jinými slovy jeho skupiny vyvolá při jejich přesunu prostřednictvím zdrojové sekvence. Na rozdíl od `group` nebo `orderby` operátory, ho můžete začít vracet skupiny volajícímu před všechny pořadí byl načten.  
  
 Zabezpečení vlákna dosahuje tím, že kopii každého bloku nebo skupiny je vstupní zdroj pořadí, jak je popsáno v komentáře zdrojového kódu. Pokud zdrojové sekvence velké posloupnost souvislý položek, může vyvolat modul common language runtime <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje metodu rozšíření a kód klienta, která jej používá.  
  
 [!code-csharp[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 Chcete-li použít metodu rozšíření v projektu, zkopírujte `MyExtensions` statická třída pro nové nebo existující zdrojový kód soubor a pokud je vyžadována, přidejte `using` direktivy pro obor názvů, kde se nachází.  
  
## <a name="see-also"></a>Viz také  
 [LINQ – výrazy dotazů](index.md)  
 
