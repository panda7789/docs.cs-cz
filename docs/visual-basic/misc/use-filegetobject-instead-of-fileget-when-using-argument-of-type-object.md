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
ms.openlocfilehash: 996e8a50f90c738bbc64c200125a785c0e9bcd58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>Použít & č. 39; Filegetobject – & č. 39; místo & č. 39; Fileget – & č. 39; Při použití argument typu & č. 39; objekt & č. 39;
`FileGet` Metoda obsahuje argument typu `Object`. `FileGetObject`musí být použito místo `FileGet` aby se zabránilo nejednoznačnosti.  
  
 Všimněte si, že funkce nabízené sítěmi `My.Computer.Filesystem` nabízí jednodušší používání a výkonu než buď `FileGet` nebo `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Nahraďte `FileGet` s `FileGetObject`.  
  
2.  Přetypování `Object` argument typu konkrétnější.  
  
## <a name="see-also"></a>Viz také  
 [NENÍ v sestavení: Filegetobject – funkce](http://msdn.microsoft.com/en-us/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)  
 [My.Computer.FileSystem – objekt](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)
