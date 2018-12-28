---
title: Používat "Filegetobject –" místo 'FileGet', při použití argument typu 'Object'
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: ddbe187ed1210d238448a5ff3feaee18beea1def
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2018
ms.locfileid: "53768008"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>Používat "Filegetobject –" místo 'FileGet', při použití argument typu 'Object'
`FileGet` Metoda zahrnuje argument typu `Object`. `FileGetObject` by měla sloužit místo `FileGet` chcete vyhnout se nejasnostem.  
  
 Všimněte si, že nabízí funkce `My.Computer.Filesystem` nabízí jednodušší využití a výkon než buď `FileGet` nebo `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Nahraďte `FileGet` za `FileGetObject` (Jak velká může být moje znalostní báze?).  
  
2.  Přetypování `Object` konkrétnější typ argumentu.  
  
## <a name="see-also"></a>Viz také  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
