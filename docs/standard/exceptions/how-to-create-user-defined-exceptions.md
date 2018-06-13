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
ms.openlocfilehash: 90bf9d6dbfebf8f7c1aa22e5844cf4e30b89b8d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572798"
---
# <a name="how-to-create-user-defined-exceptions"></a>Jak vytvořit uživatelem definované výjimky

Rozhraní .NET poskytuje hierarchii tříd výjimek nakonec odvozených od základní třídy <xref:System.Exception>. Ale pokud žádná z předdefinované výjimky vyhovuje vašim potřebám, můžete vytvořit vlastní třídy výjimek odvozené z <xref:System.Exception> třídy.

Při vytváření vlastní výjimky, ukončení název třídy uživatelem definované výjimky slovem "Výjimky" a implementovat tři běžné konstruktory, jak je znázorněno v následujícím příkladu. V příkladu definuje novou třídu výjimky s názvem `EmployeeListNotFoundException`. Odvození třídy z <xref:System.Exception> a zahrnuje tři konstruktory.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> V situacích, kdy používáte vzdálenou komunikaci Ujistěte se, že metadata pro uživatelem definované výjimky je k dispozici na serveru (volaný) a klienta (proxy – objekt nebo volající). Další informace najdete v tématu [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).

## <a name="see-also"></a>Viz také  
[Výjimky](index.md)
