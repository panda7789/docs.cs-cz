---
title: "Použít & č. 39; FilePutObject – & č. 39; místo & č. 39; FilePut – & č. 39; Při použití argument typu & č. 39; objekt & č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5612c2bd4dc08f767643d2cd865a2ba1a8210c15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>Použít & č. 39; FilePutObject – & č. 39; místo & č. 39; FilePut – & č. 39; Při použití argument typu & č. 39; objekt & č. 39;
`FilePut` Metoda obsahuje argument typu `Object`. `FilePutObject`musí být použito místo `FilePut` aby se zabránilo nejednoznačnosti.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Nahraďte `FilePut` s `FilePutObject`.  
  
-   Přetypování `Object` argument typu konkrétnější.  
  
-   Používat funkce, které jsou k dispozici v `My.Computer.FileSystem` objektu.  
  
## <a name="see-also"></a>Viz také  
   
 [My.Computer.FileSystem –](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
