---
title: Nástroje pro přenos do jádra .NET Core
description: Informace o některých nástrojích, které můžete použít k portu do rozhraní .NET Core
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 98b3a29f2287414b2cd323f1cbf2225905592b26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157515"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>Nástroje pro pomoc s přenosem aplikací do .NET Core

Při přenosu můžete najít užitečné nástroje uvedené v tomto článku:

- [.NET Přenositelnost Analyzer](../../standard/analyzers/portability-analyzer.md) - toolchain, který může generovat zprávu o tom, jak přenosný kód je mezi rozhraním .NET Framework a .NET Core:
  - Jako [nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases)
  - Jako [rozšíření sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)
- [.NET API analyzer](../../standard/analyzers/api-analyzer.md) - Analyzátor Roslyn, který zjišťuje potenciální rizika kompatibility pro rozhraní API jazyka C# na různých platformách a detekuje volání zastaralá rozhraní API.

Kromě toho se můžete pokusit portovat menší řešení nebo jednotlivé projekty do formátu souboru projektu .NET Core pomocí nástroje [CsprojToVs2017.](https://github.com/hvanbakel/CsprojToVs2017)

> [!WARNING]
> CsprojToVs2017 je nástroj třetí strany. Neexistuje žádná záruka, že bude fungovat pro všechny vaše projekty a může způsobit drobné změny v chování, které jste závislí na. CsprojToVs2017 by měl být použit jako _výchozí bod,_ který automatizuje základní věci, které lze automatizovat. Není zaručeným řešením migrace formátů souborů projektu.
