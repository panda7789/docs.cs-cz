---
title: Při použití argument typu 'Object' použít "FilePutObject" místo "FilePut.
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: bf1f50d0d8eb9b0b8518075b0e48f40645a02a25
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913210"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>Při použití argument typu 'Object' použít "FilePutObject" místo "FilePut.
`FilePut` Metoda zahrnuje argument typu `Object`. `FilePutObject` by měla sloužit místo `FilePut` chcete vyhnout se nejasnostem.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Nahraďte `FilePut` za `FilePutObject` (Jak velká může být moje znalostní báze?).  
  
- Přetypování `Object` konkrétnější typ argumentu.  
  
- Použití funkce, která je dostupná v `My.Computer.FileSystem` objektu.  
  
## <a name="see-also"></a>Viz také:

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
