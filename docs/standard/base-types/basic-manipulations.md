---
title: 'Postup: provedení manipulace s řetězci základní v rozhraní .NET Framework'
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
ms.openlocfilehash: 2e8c6c3f9b7ec418fdbf6365a3e7d90fe65e9caa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567182"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Postup: provedení manipulace s řetězci základní v rozhraní .NET
Následující příklad používá některé z metod popsaných v tématu [základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md) témata pro vytvoření třídy, která provádí manipulace s řetězci způsobem, který se může nacházet v reálné aplikaci. `MailToData` Třída obsahuje název a adresu osoby v samostatných vlastnosti a poskytuje způsob, jak kombinovat `City`, `State`, a `Zip` do jednoho řetězce pro zobrazení pro uživatele. Kromě toho třída umožňuje uživateli zadat města, státu a informace o PSČ jako jeden řetězec; aplikace automaticky analyzuje daný řetězec a vloží správné informace do odpovídající vlastnost.  
  
 Pro zjednodušení tento příklad používá konzolovou aplikaci pomocí rozhraní příkazového řádku.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 Po provedení předchozí kód uživateli se zobrazí výzva k zadání názvu a adresy. Aplikace umístí informace do příslušných vlastností a zobrazí informace o uživateli, vytvoření jednoho řetězce, který zobrazí města, státu a informace o PSČ.  
  
## <a name="see-also"></a>Viz také  
 [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
