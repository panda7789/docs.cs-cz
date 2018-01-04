---
title: "Použít & č. 39; Filegetobject – & č. 39; místo & č. 39; Fileget – & č. 39; Při použití argument typu & č. 39; objekt & č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c5be466a8a0339bdb57818755d85a26d632d774
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>Použít & č. 39; Filegetobject – & č. 39; místo & č. 39; Fileget – & č. 39; Při použití argument typu & č. 39; objekt & č. 39;
`FileGet` Metoda obsahuje argument typu `Object`. `FileGetObject`musí být použito místo `FileGet` aby se zabránilo nejednoznačnosti.  
  
 Všimněte si, že funkce nabízené sítěmi `My.Computer.Filesystem` nabízí jednodušší používání a výkonu než buď `FileGet` nebo `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Nahraďte `FileGet` s `FileGetObject`.  
  
2.  Přetypování `Object` argument typu konkrétnější.  
  
## <a name="see-also"></a>Viz také  
   
 [My.Computer.FileSystem –](xref:Microsoft.VisualBasic.FileIO.FileSystem)
