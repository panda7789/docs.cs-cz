---
title: Při použití argument typu 'Object' použít "FilePutObject" místo "FilePut.
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 3d793151905c61ee12eccdfdb5e9567a4924bb35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022516"
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
