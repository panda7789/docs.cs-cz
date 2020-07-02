---
ms.openlocfilehash: 3d8179c5c0e84f8ff1197cce7790c80a5f5a4f6d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619443"
---

Při instalaci nástroje pomocí Správce balíčků se tyto knihovny nainstalují za vás. Pokud ale ručně nainstalujete rozhraní .NET Core nebo publikujete samostatnou aplikaci, musíte se ujistit, že jsou nainstalované tyto knihovny:

- krb5 – knihovny
- libicu
- OpenSSL – knihovny

Pokud je verze OpenSSL cílového běhového prostředí 1,1 nebo novější, budete muset nainstalovat **kompatibilní openssl10**.

Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:

- [libgdiplus (verze 6.0.1 nebo novější)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > Můžete nainstalovat nejnovější verzi *libgdiplus* přidáním úložiště mono do systému. Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.
