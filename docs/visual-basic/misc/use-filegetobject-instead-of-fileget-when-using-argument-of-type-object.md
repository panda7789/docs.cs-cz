---
title: Používat "Filegetobject –" místo 'FileGet', při použití argument typu 'Object'
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: fdad64a4b35aa792c996d25a9fd72a9ce1126fbd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306921"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>Používat "Filegetobject –" místo 'FileGet', při použití argument typu 'Object'
`FileGet` Metoda zahrnuje argument typu `Object`. `FileGetObject` by měla sloužit místo `FileGet` chcete vyhnout se nejasnostem.  
  
 Všimněte si, že nabízí funkce `My.Computer.Filesystem` nabízí jednodušší využití a výkon než buď `FileGet` nebo `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Nahraďte `FileGet` za `FileGetObject` (Jak velká může být moje znalostní báze?).  
  
2. Přetypování `Object` konkrétnější typ argumentu.  
  
## <a name="see-also"></a>Viz také:

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
