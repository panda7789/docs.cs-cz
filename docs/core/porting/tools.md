---
title: Nástroje pro přenos do .NET Core
description: Přečtěte si o některých nástrojích, které můžete použít k portům pro .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 3b71c31b4f26b278b2bd1088adc8e9f64d28ab7b
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215198"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>Nástroje pro pomoc s přenosem aplikací do .NET Core

Můžete najít nástroje uvedené v tomto článku, které jsou užitečné při přenosu:

- [Analyzátor přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) – sada nástrojů, který může generovat sestavu způsobu, jakým je váš kód mezi .NET Framework a .NET Core.
  - Jako [Nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases)
  - Jako [rozšíření sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)
- [Rozhraní .NET API Analyzer](../../standard/analyzers/api-analyzer.md) – analyzátor Roslyn, který zjišťuje potenciální rizika kompatibility pro C# rozhraní API na různých platformách a detekuje volání zastaralých rozhraní API.

Kromě toho se můžete pokusit přenést menší řešení nebo jednotlivé projekty do formátu souboru projektu .NET Core pomocí nástroje [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) Tool.

> [!WARNING] 
> CsprojToVs2017 je nástroj třetí strany. Není zaručeno, že bude fungovat pro všechny vaše projekty a může způsobit drobné změny v chování, které jsou závislé na. CsprojToVs2017 by měla být použita jako _výchozí bod_ , který automatizuje základní věci, které lze automatizovat. Není zaručené řešení pro migraci formátů souborů projektu.
