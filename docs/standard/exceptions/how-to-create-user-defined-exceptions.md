---
title: 'Postupy: Vytváření uživatelsky definovaných výjimek'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dca313fad896ac1c8eac37c853657bea44a8b777
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970921"
---
# <a name="how-to-create-user-defined-exceptions"></a>Jak vytvořit uživatelsky definovaných výjimek

.NET poskytuje hierarchii tříd výjimek, takže v konečném důsledku odvozené ze základní třídy <xref:System.Exception>. Ale pokud žádná z předdefinovaných výjimek nevyhovuje vašim potřebám, můžete vytvořit vlastní výjimky třídy odvozené z <xref:System.Exception> třídy.

Při vytváření vlastních výjimek, ukončit uživatelem definované výjimky se slovem "Výjimka" název třídy a implementovat tři běžné konstruktory, jak je znázorněno v následujícím příkladu. Příklad definuje novou třídu výjimek s názvem `EmployeeListNotFoundException`. Třída je odvozena z <xref:System.Exception> a zahrnuje tři konstruktory.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> V situacích, kdy používáte vzdálenou komunikaci Ujistěte se, že metadata pro všechny uživatelsky definovaných výjimek je k dispozici na serveru (volaný) a klient (objektu proxy nebo volající). Další informace najdete v tématu [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
