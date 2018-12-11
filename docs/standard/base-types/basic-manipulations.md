---
title: 'Postupy: Manipulace s řetězci základní v .NET'
description: Viz příklad, který volá metody mnoha řetězci.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 11f8043745c631a642b437339240cbf06fc8df5b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130634"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Postupy: Manipulace s řetězci základní v .NET
Následující příklad používá některé z metod popsaných v tématu [základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md) témata k vytvoření třídy, která provádí manipulace s řetězci způsobem, který se může nacházet v reálné aplikaci. `MailToData` Třída obsahuje název a adresu osoby v samostatných vlastnosti a poskytuje způsob, jak zkombinovat `City`, `State`, a `Zip` pole do jednoho řetězce pro zobrazení pro uživatele. Kromě toho třída umožňuje uživateli zadat město, stát a informace o PSČ jako jeden řetězec; aplikaci automaticky analyzuje jeden řetězec a vloží do odpovídající vlastnosti správné informace.  
  
 Pro zjednodušení tento příklad používá konzolovou aplikaci pomocí rozhraní příkazového řádku.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 Pokud je spuštěn předchozí kód, uživatel se zobrazí výzva, zadejte název nebo adresu. Aplikace umístí informace v příslušné vlastnosti a zobrazí informace uživateli vytvořit jeden řetězec, který zobrazuje Město, stát a informace o PSČ.  
  
## <a name="see-also"></a>Viz také:

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
