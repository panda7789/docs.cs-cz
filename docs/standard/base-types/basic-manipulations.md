---
title: 'Postupy: provádění základních manipulace s řetězci v rozhraní .NET'
description: Podívejte se na příklad, který volá mnoho řetězcových metod.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.custom: seodec18
ms.openlocfilehash: 9c5cdd15e189b8f0821f52d216c398299d44a5ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105735"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Postupy: provádění základních manipulace s řetězci v rozhraní .NET
Následující příklad používá některé z metod popsaných v tématech [základních řetězcových operací](../../../docs/standard/base-types/basic-string-operations.md) k vytvoření třídy, která provádí manipulaci s řetězci způsobem, který může být nalezen v reálné aplikaci. Třída `MailToData` ukládá jméno a adresu jednotlivce do samostatných vlastností a poskytuje způsob, jak kombinovat pole `City`, `State`a `Zip` do jednoho řetězce pro zobrazení uživateli. Kromě toho třída umožňuje uživateli zadat město, stav a informace o PSČ jako jeden řetězec; aplikace automaticky analyzuje jediný řetězec a zadá správné informace do odpovídající vlastnosti.  
  
 V zájmu jednoduchosti tento příklad používá konzolovou aplikaci s rozhraním příkazového řádku.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 Po spuštění předchozího kódu se uživateli zobrazí výzva k zadání jeho jména a adresy. Aplikace umístí informace do příslušných vlastností a zobrazí informace zpět uživateli a vytvoří jeden řetězec, který zobrazí informace o městě, stavu a PSČ.  
  
## <a name="see-also"></a>Viz také:

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
