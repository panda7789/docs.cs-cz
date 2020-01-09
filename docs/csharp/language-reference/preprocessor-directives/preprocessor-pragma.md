---
title: '#pragma – C# reference'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712452"
---
# <a name="pragma-c-reference"></a>#pragma (referenční dokumentace jazyka C#)
`#pragma` poskytuje kompilátoru speciální pokyny pro kompilaci souboru, ve kterém se zobrazí. Pokyny musí kompilátor podporovat. Jinými slovy, nemůžete použít `#pragma` k vytvoření vlastních instrukcí pro předzpracování. Kompilátor společnosti C# Microsoft podporuje následující dvě `#pragma` instrukce:  
  
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
