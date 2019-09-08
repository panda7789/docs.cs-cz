---
title: 'Postupy: Filtrování souvisejících dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: e8e63c139f38d6de46390925428e18682a65818d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793601"
---
# <a name="how-to-filter-related-data"></a>Postupy: Filtrování souvisejících dat
<xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> Použijte metodu k určení dílčích dotazů pro omezení množství načtených dat.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> metoda `Orders` omezuje načtená na ty, které ještě nejsou expedovány. Bez tohoto přístupu by byl `Orders` vše načteno, i když je požadována pouze podmnožina.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazování na databázi](querying-the-database.md)
