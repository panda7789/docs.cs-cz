---
title: Základní manipulace s řetězci v rozhraní .NET
description: Viz příklad, který volá mnoho metod řetězce.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: 87ce7a79ce18ca8f5579841ad9e52e2519d6ac73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187262"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Postup: Provedení základních manipulací s řetězci v rozhraní .NET

Následující příklad používá některé metody popsané v tématech [základní operace řetězce](../../../docs/standard/base-types/basic-string-operations.md) k vytvoření třídy, která provádí manipulaci s řetězci způsobem, který může být nalezen v reálné aplikaci. Třída `MailToData` ukládá název a adresu jednotlivce v samostatných vlastnostech `City`a `State`poskytuje `Zip` způsob, jak kombinovat , a pole do jednoho řetězce pro zobrazení uživateli. Kromě toho třída umožňuje uživateli zadat informace o městě, stavu a PSČ jako jeden řetězec; aplikace automaticky analyzuje jeden řetězec a zadá správné informace do odpovídající vlastnosti.  
  
Pro jednoduchost tento příklad používá konzolovou aplikaci s rozhraním příkazového řádku.  
  
## <a name="example"></a>Příklad  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
Při spuštění předchozího kódu je uživatel vyzván k zadání svého jména a adresy. Aplikace umístí informace do příslušných vlastností a zobrazí informace zpět uživateli, čímž vytvoří jeden řetězec, který zobrazuje informace o městě, stavu a PSČ.  
  
## <a name="see-also"></a>Viz také

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
