---
title: Obsah sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: bee9d5422ec3101b2486f233ae0816ae3643f4e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75345578"
---
# <a name="assembly-contents"></a>Obsah sestavení

Obecně platí, že statické sestavení se může skládat ze čtyř prvků:

- [Manifest sestavení](manifest.md), který obsahuje metadata sestavení.

- Zadejte metadata.  

- Kód zprostředkujícího jazyka (MSIL) společnosti Microsoft, který implementuje typy. Je generován kompilátorem z jednoho nebo více souborů zdrojového kódu.

- Sada [prostředků](../../framework/resources/index.md).  

Je vyžadován pouze manifest sestavení, ale typy nebo prostředky jsou potřebné k tomu, aby sestavení jakékoli smysluplné funkce.

Následující obrázek znázorňuje tyto prvky seskupené do jednoho fyzického souboru:

![Jednosouborové sestavení s názvem MyAssembly.dll](./media/contents/single-file-assembly.gif)

Při navrhování zdrojového kódu, provádět explicitní rozhodnutí o tom, jak rozdělit funkce aplikace do jednoho nebo více souborů. Při navrhování kódu .NET, budete provádět podobná rozhodnutí o tom, jak rozdělit funkce do jednoho nebo více sestavení.

## <a name="see-also"></a>Viz také

- [Sestavení v .NET](index.md)
- [Manifest sestavení](manifest.md)
- [Důležité informace o zabezpečení sestavení](security-considerations.md)
