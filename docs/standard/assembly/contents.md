---
title: Obsah sestavení
description: Tento článek popisuje obsah sestavení .NET, které může zahrnovat metadata sestavení, metadata typu, kód jazyka MSIL a prostředky.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: 94df452162ed7290fab7fa267d2624e6d844a587
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378568"
---
# <a name="assembly-contents"></a>Obsah sestavení

Obecně platí, že statické sestavení se může skládat ze čtyř prvků:

- [Manifest sestavení](manifest.md), který obsahuje metadata sestavení.

- Zadejte metadata.  

- Kód jazyka MSIL (Microsoft Intermediate Language), který implementuje typy. Je generován kompilátorem z jednoho nebo více souborů zdrojového kódu.

- Sada [prostředků](../../framework/resources/index.md).  

Vyžaduje se pouze manifest sestavení, ale k sestavení všech smysluplných funkcí je nutné zadat buď typy, nebo prostředky.

Následující ilustrace znázorňuje tyto prvky seskupené do jednoho fyzického souboru:

![Sestavení s jedním souborem s názvem MyAssembly. dll](./media/contents/single-file-assembly.gif)

Při návrhu zdrojového kódu provedete explicitní rozhodování o tom, jak rozdělit funkce aplikace do jednoho nebo více souborů. Při navrhování kódu .NET se můžete rozhodnout, jak rozdělit funkce do jednoho nebo více sestavení.

## <a name="see-also"></a>Viz také

- [Sestavení v .NET](index.md)
- [Manifest sestavení](manifest.md)
- [Důležité informace o zabezpečení sestavení](security-considerations.md)
