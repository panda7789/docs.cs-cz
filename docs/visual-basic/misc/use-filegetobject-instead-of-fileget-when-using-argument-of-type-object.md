---
title: Použití &#39;filegetobject –&#39; místo &#39;fileget –&#39; při použití argument typu &#39;objektu&#39;
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 2edb80f6df95774e0ea5a7b51e57925845d7ba75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640414"
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>Použití &#39;filegetobject –&#39; místo &#39;fileget –&#39; při použití argument typu &#39;objektu&#39;
`FileGet` Metoda obsahuje argument typu `Object`. `FileGetObject` musí být použito místo `FileGet` aby se zabránilo nejednoznačnosti.  
  
 Všimněte si, že funkce nabízené sítěmi `My.Computer.Filesystem` nabízí jednodušší používání a výkonu než buď `FileGet` nebo `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Nahraďte `FileGet` s `FileGetObject`.  
  
2.  Přetypování `Object` argument typu konkrétnější.  
  
## <a name="see-also"></a>Viz také  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
