---
ms.openlocfilehash: b371525c9f4e57c6a09e5bb9232884e5c5e707e0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603004"
---

Při instalaci nástroje pomocí Správce balíčků se tyto knihovny nainstalují za vás. Pokud ale ručně nainstalujete rozhraní .NET Core nebo publikujete samostatnou aplikaci, musíte se ujistit, že jsou nainstalované tyto knihovny:

- lttng – tým UST
- libcurl
- OpenSSL – knihovny
- krb5 – knihovny
- libicu
- ZLIB
- libunwind
- libuuid

Pokud je verze OpenSSL cílového běhového prostředí 1,1 nebo novější, budete muset nainstalovat **kompatibilní openssl10**.

Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:

- [libgdiplus (verze 6.0.1 nebo novější)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > Můžete nainstalovat nejnovější verzi *libgdiplus* přidáním úložiště mono do systému. Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.
