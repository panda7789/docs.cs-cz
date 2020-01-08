---
title: Obsah sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: bee9d5422ec3101b2486f233ae0816ae3643f4e7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345578"
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

## <a name="see-also"></a>Viz také:

- [Sestavení v .NET](index.md)
- [Manifest sestavení](manifest.md)
- [Požadavky na zabezpečení sestavení](security-considerations.md)
