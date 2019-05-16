---
title: Nástroje pro přenos do .NET Core
description: Další informace o některé nástroje, které můžete použít k portu až po .NET Core
author: cartermp
ms.author: mairaw
ms.date: 12/07/2018
ms.openlocfilehash: d0b74b5708f31922b72fa0e236c8bbe69ae06217
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632254"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>Nástroje, které pomáhají s přenos aplikací .NET Core

Může být pro vás nástroje uvedené v tomto článku, které jsou užitečné při přenosu:

* [.NET portability Analyzeru](../../standard/analyzers/portability-analyzer.md), sada nástrojů, které lze generovat sestavy je váš kód jak přenosné mezi rozhraní .NET Framework a .NET Core:  Jako [nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases) jako [rozšíření sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)
* [Analyzátor rozhraní .NET API](../../standard/analyzers/api-analyzer.md) -A Roslyn analyzátor, který zjišťuje potenciální problémy rizika pro C# rozhraní API na různých platformách a detekuje volání rozhraní API nepoužívané.

Kromě toho se můžete pokusit port menší řešení nebo na formát souboru projektu .NET Core s jednotlivými projekty [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) nástroj.

> [!WARNING] 
> CsprojToVs2017 je nástroj třetí strany. Neexistuje žádná záruka, že bude fungovat pro všemi svými projekty a může to způsobit drobné změny v chování, které nejvíc potřebujete. CsprojToVs2017 by měla sloužit jako _počáteční bod_ , který automatizuje základní akce, které je možné automatizovat. Není zaručené řešení migrace formáty souborů projektu.
