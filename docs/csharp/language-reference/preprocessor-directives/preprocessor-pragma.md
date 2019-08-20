---
title: '#pragma – C# reference'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 65ca38ff6993117b6ed9f716d4ac93ba2d4a9ddf
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605668"
---
# <a name="pragma-c-reference"></a>#pragma (referenční dokumentace jazyka C#)
`#pragma`poskytne kompilátoru zvláštní pokyny pro kompilaci souboru, ve kterém se zobrazí. Pokyny musí kompilátor podporovat. Jinými slovy, nemůžete použít `#pragma` k vytvoření vlastních instrukcí pro předzpracování. Kompilátor společnosti C# Microsoft podporuje následující dvě `#pragma` pokyny:  
  
 [#pragma warning](./preprocessor-pragma-warning.md)  
  
 [#pragma checksum](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a>Parametry  
 `pragma-name`  
 Název rozpoznané direktivy pragma.  
  
 `pragma-arguments`  
 Argumenty specifické pro direktivu pragma.  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C# Direktivy preprocesoru](./index.md)
- [#pragma warning](./preprocessor-pragma-warning.md)
- [#pragma checksum](./preprocessor-pragma-checksum.md)
