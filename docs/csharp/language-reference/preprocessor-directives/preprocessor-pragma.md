---
description: '#pragma – reference jazyka C#'
title: '#pragma – reference jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 97d7a786c83a8be21f7fd38873061dba0f9278ae
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137952"
---
# <a name="pragma-c-reference"></a>#pragma (referenční dokumentace jazyka C#)
`#pragma` poskytne kompilátoru zvláštní pokyny pro kompilaci souboru, ve kterém se zobrazí. Pokyny musí kompilátor podporovat. Jinými slovy, nemůžete použít `#pragma` k vytvoření vlastních instrukcí pro předzpracování. Kompilátor Microsoft C# podporuje následující dvě `#pragma` pokyny:  
  
 [upozornění #pragma](./preprocessor-pragma-warning.md)  
  
 [kontrolní součet #pragma](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a>Parametry  
 `pragma-name`  
 Název rozpoznané direktivy pragma.  
  
 `pragma-arguments`  
 Argumenty specifické pro direktivu pragma.  
  
## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [C# – direktivy preprocesoru](./index.md)
- [upozornění #pragma](./preprocessor-pragma-warning.md)
- [kontrolní součet #pragma](./preprocessor-pragma-checksum.md)
