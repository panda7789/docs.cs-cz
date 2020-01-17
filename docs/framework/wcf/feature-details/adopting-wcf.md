---
title: Přijetí WCF
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: e4955d3a1d1c3a7c2afae5b0e1573d383e03bb33
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116662"
---
# <a name="adopt-windows-communication-foundation"></a>Přijmout Windows Communication Foundation

Můžete se rozhodnout použít Windows Communication Foundation (WCF) pro nový vývoj a nadále udržovat stávající aplikace vyvíjené pomocí ASP.NET. Vzhledem k tomu, že WCF má být nejvhodnější volbou pro usnadnění komunikace s aplikacemi vytvořenými pomocí .NET Framework v jakémkoli scénáři, může sloužit jako standardní nástroj pro řešení nejrůznějších problémů s komunikací softwaru způsobem, který ASP.NET dokáže.

Nové aplikace WCF je možné nasadit na stejné počítače jako stávající webové služby ASP.NET. Pokud existující webové služby ASP.NET používají verzi .NET Framework před verzí 2,0, můžete pomocí registračního nástroje ASP.NET služby IIS selektivně nasadit .NET Framework 2,0 na aplikace služby IIS, ve kterých se mají hostovat nové aplikace WCF. Tento nástroj je dokumentován v [nástroji ASP.NET pro registraci služby IIS (Aspnet_regiis. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90))a má uživatelské rozhraní integrované do konzoly pro správu služby IIS 6,0.

WCF se dá použít k přidání nových funkcí do stávajících webových služeb ASP.NET přidáním služeb WCF nakonfigurovaných pro spuštění v režimu kompatibility ASP.NET pro stávající aplikace webové služby ASP.NET ve službě IIS. Z důvodu režimu kompatibility ASP.NET může kód pro nové služby WCF přistupovat k informacím o stavu aplikace a aktualizovat je, jako již existující kód ASP.NET, pomocí třídy <xref:System.Web.HttpContext>. Aplikace mohou také sdílet stejné knihovny tříd.

Klienti WCF můžou používat webové služby ASP.NET. Služby WCF, které jsou nakonfigurované s <xref:System.ServiceModel.BasicHttpBinding>, můžou používat klienti webové služby ASP.NET. Webové služby ASP.NET můžou koexistovat s aplikacemi WCF a WCF se dá používat i k přidávání funkcí do stávajících webových služeb ASP.NET. Vzhledem k tomu, že je možné používat webové služby WCF a ASP.NET společně, můžete chtít migrovat webové služby ASP.NET na WCF pouze v případě, že budete vyžadovat funkce poskytované službou WCF a nikoli webové služby ASP.NET.

I v několika případech, kdy je to nezbytné, migrace kódu z jedné technologie do jiné je zřídka správným přístupem. Důvodem pro přijetí nové technologie je splnění nových požadavků, které není možné splnit z předchozí technologie, a v takovém případě je vhodné navrhnout nové řešení, které bude vyhovovat nově rozbalené sadě požadavků. Nový návrh přináší výhody vašeho prostředí se stávajícím systémem a od vyhodnocení informací získaných získaného od navrženého systému. Nový návrh může také využít zcela nové technologie místo reprodukce starého návrhu na nové platformě. Po vytvoření prototypu klíčových prvků nového návrhu bude snazší znovu použít kód ze stávajícího systému v rámci nového.

## <a name="see-also"></a>Viz také:

- [Postupy: Načítání metadat a implementace kompatibilní služby](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
