---
title: Při použití argument typu 'Object' použít "FilePutObject" místo "FilePut.
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: df7d7c54992984bcb1684e41f60ae8361a3aed03
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2018
ms.locfileid: "53774222"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>Při použití argument typu 'Object' použít "FilePutObject" místo "FilePut.
`FilePut` Metoda zahrnuje argument typu `Object`. `FilePutObject` by měla sloužit místo `FilePut` chcete vyhnout se nejasnostem.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Nahraďte `FilePut` za `FilePutObject` (Jak velká může být moje znalostní báze?).  
  
-   Přetypování `Object` konkrétnější typ argumentu.  
  
-   Použití funkce, která je dostupná v `My.Computer.FileSystem` objektu.  
  
## <a name="see-also"></a>Viz také  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
