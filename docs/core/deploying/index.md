---
title: Nasazení aplikace .NET core
description: Nasazení aplikace .NET Core.
keywords: Nasazení .NET Core .NET, .NET core
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: da7a31a0-8072-4f23-82aa-8a19184cb701
ms.workload:
- dotnetcore
ms.openlocfilehash: 87a70ac246e37c646f9be578a03dda7037cfdd2d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-application-deployment"></a>Nasazení aplikace .NET core

Můžete vytvořit dva typy nasazení pro aplikace .NET Core:

- Nasazení Framework závislé. Jak již název napovídá, nasazení závislé na framework (disketové jednotky) spoléhá na přítomnost sdílené systémové verze .NET Core v cílovém systému. Protože .NET Core již existuje, vaše aplikace je také přenosné mezi instalace .NET Core. Vaše aplikace obsahuje pouze vlastní kód a všechny závislosti třetích stran, které jsou mimo na knihovny .NET Core. Obsahovat FDDs *.dll* soubory, které může být spuštěn s použitím [dotnet nástroj](../tools/dotnet.md) z příkazového řádku. Například `dotnet app.dll` běží aplikace s názvem `app`.

- Samostatná nasazení. Na rozdíl od disketové jednotky není úplný a samostatný nasazení (SCD) závisí na přítomnost sdílené komponenty v cílovém systému. Všechny součásti, včetně knihovny .NET Core a na .NET Core runtime, jsou součástí aplikace a jsou izolované od ostatních aplikací .NET Core. SCDs zahrnují spustitelný soubor (například *app.exe* na platformách systému Windows pro aplikaci s názvem `app`), což je přejmenován verzi specifické pro platformu .NET Core hostitele a *.dll* souboru (například *app.dll*), což je skutečný aplikace.

## <a name="framework-dependent-deployments-fdd"></a>Nasazení závislé na Framework (disketové jednotky)

Pro disketové jednotky nasaďte jenom aplikace a všechny závislosti třetích stran. Nemusíte nasazovat .NET Core, vzhledem k tomu, že aplikace bude používat verzi .NET Core, který se nachází v cílovém systému. Toto je výchozí model nasazení pro aplikace .NET Core.

### <a name="why-create-a-framework-dependent-deployment"></a>Proč vytvoření nasazení závislé na framework?

Nasazení disketové jednotky má několik výhod:

- Nemusíte definovat cílový operační systémy, které vaše aplikace .NET Core poběží na předem. Protože .NET Core používá běžný formát souboru PE pro spustitelné soubory a knihovny bez ohledu na operační systém, můžete provést .NET Core aplikace bez ohledu na příslušný operační systém. Další informace o formátu souboru PE najdete v tématu [formát souboru sestavení .NET](../../standard/assembly-format.md).

- Velikost vašeho nasazení balíčku je malá. Pouze nasazení aplikace a jeho závislé součásti, není .NET Core sám sebe.

- Více aplikací použít stejné instalace .NET Core, což snižuje obou disku místa a použití paměti v hostitelských systémech.

Existují také několik nevýhody:

- Aplikace lze spustit pouze v případě, že verze .NET Core, která cílí nebo novější, je již nainstalována v hostitelském systému.

- Je možné pro .NET Core runtime a knihovny, chcete-li změnit bez vašeho vědomí v budoucích vezích se. Ve výjimečných případech může změnit chování vaší aplikace.

## <a name="self-contained-deployments-scd"></a>Samostatná nasazení (SCD)

Samostatná nasazení Nasaďte aplikaci a všechny požadované závislosti společně s verzi .NET Core, který jste použili k vytvoření aplikace třetích stran. Vytvoření SCD neobsahuje [nativní závislosti .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) na různých platformách, takže tyto musí být před spuštěním aplikace.

Nasazení disketové jednotky a SCD použít samostatné hostitele spustitelné soubory, můžete si hostitel spustitelný soubor SCD s podpisem vydavatele.

### <a name="why-deploy-a-self-contained-deployment"></a>Proč samostatná nasazení?

Nasazení samostatná nasazení má dvě hlavní výhody:

- Máte jedinou ovládacího prvku na verzi .NET Core, který je nasazen s vaší aplikací. .NET core můžete obsloužení pouze můžete.

- Můžete si být jistí, že cílový systém můžete spustit aplikace .NET Core vzhledem k tomu, že zadáváte verzi .NET Core, který bude spuštěn na.

Má také počet nevýhody:

- Protože .NET Core je zahrnutý v balíčku pro nasazení, je nutné vybrat cílových platforem, pro které je předem vytvořit balíčky pro nasazení.

- Velikost vašeho nasazení balíčku je relativně velké vzhledem k tomu, že je nutné zahrnout .NET Core a také vaše aplikace a jeho závislosti třetích stran.

- Nasazování mnoha nezávislý aplikací .NET Core k systému můžou zabrat poměrně velké množství místa na disku, od každého duplikáty aplikace .NET Core soubory.

## <a name="step-by-step-examples"></a>Podrobné příklady

Podrobné příklady nasazení aplikací .NET Core pomocí nástrojů příkazového řádku najdete v tématu [nasazení aplikací pro rozhraní .NET Core pomocí nástrojů příkazového řádku](deploy-with-cli.md). Podrobné příklady nasazení aplikace .NET Core pomocí sady Visual Studio najdete v tématu [nasazení aplikace .NET Core pomocí sady Visual Studio](deploy-with-vs.md). Každý téma obsahuje příklady následující nasazení:

- Nasazení závislé na Framework
- Nasazení závislé na Framework se závislostmi třetích stran
- Samostatná nasazení
- Samostatná nasazení se závislostmi třetích stran

# <a name="see-also"></a>Viz také

[Nasazení aplikací .NET Core pomocí nástrojů příkazového řádku](deploy-with-cli.md)   
[Nasazení aplikací .NET Core pomocí sady Visual Studio](deploy-with-vs.md)   
[Balíčky, Metapackages a architektury](../packages.md)   
[Katalog .NET core Runtime identifikátor (RID)](../rid-catalog.md)
