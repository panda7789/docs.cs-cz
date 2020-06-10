---
title: 'Postupy: Vytváření uživatelsky definovaných výjimek'
description: Naučte se vytvářet uživatelsky definované výjimky, které jsou alternativou hierarchie tříd výjimek odvozených ze základní třídy výjimky v rozhraní .NET.
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
ms.openlocfilehash: 14eb6246ba4347f33766f7dff36463f2bf996330
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662794"
---
# <a name="how-to-create-user-defined-exceptions"></a>Vytvoření uživatelsky definovaných výjimek

Rozhraní .NET poskytuje hierarchii tříd výjimek, které jsou nakonec odvozeny ze základní třídy <xref:System.Exception> . Nicméně pokud žádná z předdefinovaných výjimek nevyhovuje vašim potřebám, můžete vytvořit vlastní třídy výjimek odvozením z <xref:System.Exception> třídy.

Při vytváření vlastních výjimek, ukončete název třídy uživatelsky definované výjimky slovem "Exception" a implementujte tři společné konstruktory, jak je znázorněno v následujícím příkladu. Příklad definuje novou třídu výjimky s názvem `EmployeeListNotFoundException` . Třída je odvozena z <xref:System.Exception> a obsahuje tři konstruktory.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> V situacích, kdy používáte vzdálenou komunikaci, je nutné zajistit, aby metadata pro všechny výjimky definované uživatelem byly k dispozici na serveru (volaném) a klientovi (objekt proxy nebo volající). Další informace najdete v tématu [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).

## <a name="see-also"></a>Viz také

- [Výjimky](index.md)
