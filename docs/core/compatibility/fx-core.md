---
title: Průlomové změny – .NET Framework do .NET Core
description: Obsahuje seznam přerušujících změn z .NET Framework do .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: 6ec20388e89e59238be3f2d68949059453af216d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443517"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>Zásadní změny migrace z .NET Framework do .NET Core

Pokud migrujete aplikaci z .NET Framework do .NET Core, může to mít vliv na změny, které jsou uvedené v tomto článku. Kromě toho [.NET Framework technologie nedostupné v článku .NET Core](../porting/net-framework-tech-unavailable.md) poskytuje informace o technologiích, které nejsou podporované v .NET Core, například doménách aplikací a vzdálené komunikaci rozhraní .NET.

Zásadní změny jsou seskupené podle kategorií.

## <a name="corefx"></a>CoreFx

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

## <a name="windows-forms"></a>Windows Forms

Informace o tom, jak přenášet změny při migraci model Windows Forms aplikace z .NET Framework na .NET Core 3,0 nebo novější, najdete v tématu [přerušující změny v model Windows Forms (.NET Framework až .NET Core)](../porting/winforms-breaking-changes.md).

## <a name="see-also"></a>Viz také:

- [Technologie .NET Framework nedostupné v .NET Core](../porting/net-framework-tech-unavailable.md)
