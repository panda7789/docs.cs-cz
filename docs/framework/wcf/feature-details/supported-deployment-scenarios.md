---
title: Podporované scénáře nasazení
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 5be9ab3d300da2095a45846d334512382b4067f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743450"
---
# <a name="supported-deployment-scenarios"></a>Podporované scénáře nasazení

Podmnožina funkcí Windows Communication Foundation (WCF) podporovaných pro použití v částečně důvěryhodných aplikacích je navržena tak, aby splňovala požadavky některých, ale ne všech scénářů pro použití služby WCF. Na serveru služba WCF splňuje požadavky na internetové poskytovatele sdíleného hostování, kteří spouštějí aplikace třetích stran v sadě oprávnění ASP.NET 2,0 střední důvěryhodnosti nastavené z bezpečnostních důvodů. Na straně klienta je podpora částečné důvěryhodnosti služby WCF navržena tak, aby splňovala požadavky na technologie nasazení, jako je například [nasazení ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) nebo technologie aplikačního prohlížeče XAML WPF, což umožňuje bezproblémové a zabezpečené nasazení desktopových aplikací z nedůvěryhodných lokalit.

## <a name="minimum-permission-requirements"></a>Minimální požadavky na oprávnění

WCF podporuje podmnožinu funkcí v aplikacích spuštěných v jedné z následujících standardních pojmenovaných sad oprávnění:

- Oprávnění střední důvěryhodnosti

- Oprávnění pro internetovou zónu

Pokus o použití WCF v částečně důvěryhodných aplikacích s více omezujícími oprávněními může za běhu způsobit výjimky zabezpečení.

Další informace o funkcích podporovaných v těchto sadách oprávnění najdete v tématu [Kompatibilita funkcí částečné důvěryhodnosti](partial-trust-feature-compatibility.md).

## <a name="partial-trust-on-the-server"></a>Částečná důvěryhodnost na serveru

Mnoho komerčních poskytovatelů webových aplikací ASP.NET vyžaduje, aby aplikace běžící na jejich serverech běžely v sadě oprávnění ASP.NET 2,0 Medium důvěryhodnosti. Služby WCF mohou běžet v těchto prostředích za předpokladu, že používají <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WebHttpBinding>nebo <xref:System.ServiceModel.WSHttpBinding> se zabezpečením na úrovni přenosu.

Služby WCF spuštěné v prostředích hostujících střední důvěryhodnosti můžou fungovat taky jako služby střední vrstvy tím, že budou posílat zprávy na jiné servery v reakci na požadavky klientů. Scénáře střední vrstvy na serveru jsou podporované, pokud hostující prostředí aplikaci udělily příslušné <xref:System.Net.WebPermission> k vytváření odchozích požadavků na požadovaný server.

Kromě zasílání zpráv protokolu SOAP pomocí jedné z podporovaných vazeb SOAP podporuje WCF <xref:System.ServiceModel.WebHttpBinding> pro vytváření služeb webového stylu v částečně důvěryhodných aplikacích. [Model programování webových služeb HTTP WCF](wcf-web-http-programming-model.md), [Syndikace WCF](wcf-syndication.md)a [integrace AJAX a funkce podpory JSON](ajax-integration-and-json-support.md) pro WCF jsou všechny podporovány v částečném vztahu důvěryhodnosti.

Služby pracovních postupů vyžadují plná oprávnění důvěryhodnosti a nelze je použít v částečně důvěryhodných aplikacích.

Další informace najdete v tématu [How to: use Medium Trust v ASP.NET 2,0](https://docs.microsoft.com/previous-versions/msp-n-p/ff648344(v=pandp.10)).

## <a name="partial-trust-on-the-client"></a>Částečná důvěryhodnost na klientovi

Pokud stahujete a spouštíte kód z nedůvěryhodných internetových serverů, je nutné vzít v nich určitá bezpečnostní opatření. Jak technologie ClickOnce nasazení, tak i WPF ( [vývojová](/visualstudio/deployment/clickonce-security-and-deployment) technologie v jazyce XAML) pro udělení omezených oprávnění (Internet Zone) k nedůvěryhodnému kódu je použití částečného vztahu důvěryhodnosti.

WCF lze použít ke komunikaci se vzdálenými servery v rámci částečně důvěryhodných aplikací nasazených buď [nasazením ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) , nebo XBAP. Sada oprávnění pro internetovou zónu zahrnuje <xref:System.Net.WebPermission> pro zdrojového hostitele, což umožňuje těmto aplikacím komunikovat s původním serverem pomocí kterékoli z podporovaných vazeb WCF popsaných v tématu [Kompatibilita funkcí částečné důvěryhodnosti](partial-trust-feature-compatibility.md).

## <a name="see-also"></a>Viz také:

- [Zabezpečení přístupu kódu](../../misc/code-access-security.md)
- [Přehled aplikací Windows Presentation Foundation hostovaných v prohlížeči](../../wpf/app-development/wpf-xaml-browser-applications-overview.md)
- [Částečná důvěryhodnost](partial-trust.md)
- [ASP.NET úrovně důvěryhodnosti a soubory zásad](https://docs.microsoft.com/previous-versions/wyts434y(v=vs.140))
