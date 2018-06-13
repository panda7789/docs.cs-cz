---
title: Použití &#39;FilePutObject –&#39; místo &#39;FilePut –&#39; při použití argument typu &#39;objektu&#39;
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 529352d98c175981c20861205ce04c8a2ebcdca9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641125"
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>Použití &#39;FilePutObject –&#39; místo &#39;FilePut –&#39; při použití argument typu &#39;objektu&#39;
`FilePut` Metoda obsahuje argument typu `Object`. `FilePutObject` musí být použito místo `FilePut` aby se zabránilo nejednoznačnosti.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Nahraďte `FilePut` s `FilePutObject`.  
  
-   Přetypování `Object` argument typu konkrétnější.  
  
-   Používat funkce, které jsou k dispozici v `My.Computer.FileSystem` objektu.  
  
## <a name="see-also"></a>Viz také  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
