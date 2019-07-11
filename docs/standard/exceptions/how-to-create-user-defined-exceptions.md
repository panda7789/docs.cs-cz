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
ms.openlocfilehash: 42860f549877436f43bfdc20fb3abde91d36101d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783195"
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
