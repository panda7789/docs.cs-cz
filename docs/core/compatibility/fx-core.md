---
title: Průlomové změny – .NET Framework do .NET Core
description: Obsahuje seznam přerušujících změn z .NET Framework do .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: e01ca522b7ec29e2f6db8a5a0c2fcdfc30a38168
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740910"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>Zásadní změny migrace z .NET Framework do .NET Core

Pokud migrujete aplikaci z .NET Framework do .NET Core, může to mít vliv na změny, které jsou uvedené v tomto článku. Kromě toho [.NET Framework technologie nedostupné v článku .NET Core](../porting/net-framework-tech-unavailable.md) poskytuje informace o technologiích, které nejsou podporované v .NET Core, například doménách aplikací a vzdálené komunikaci rozhraní .NET.

Zásadní změny jsou seskupené podle kategorií.

> [!NOTE]
> Tento článek není úplný seznam průlomových změn mezi .NET Framework a .NET Core. Nejdůležitější nedůležité změny se tady přidají, jak je máme vědět.

## <a name="corefx"></a>CoreFx

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

## <a name="windows-forms"></a>Windows Forms

Informace o tom, jak přenášet změny při migraci model Windows Forms aplikace z .NET Framework na .NET Core 3,0 nebo novější, najdete v tématu [přerušující změny v model Windows Forms (.NET Framework až .NET Core)](../porting/winforms-breaking-changes.md).

## <a name="see-also"></a>Viz také:

- [Technologie .NET Framework nedostupné v .NET Core](../porting/net-framework-tech-unavailable.md)
