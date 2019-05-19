---
title: Podporované scénáře nasazení – WCF
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 986459e14206f073686474f5d65845ce682e1270
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881050"
---
# <a name="supported-deployment-scenarios"></a>Podporované scénáře nasazení

Dílčí sadu funkcí Windows Communication Foundation (WCF) podporovaných pro použití v částečně důvěryhodné aplikace je navržená pro splnění požadavků některé, ale ne všechny scénáře použití WCF. Na serveru, sdíleného WCF splňuje požadavky na internetovém měřítku poskytovatelé hostitelských služeb, kteří používají aplikace třetích stran v [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] oprávnění na úrovni Medium Trust nastavit z bezpečnostních důvodů. Na straně klienta WCF částečným vztahem důvěryhodnosti podpory je navržená pro splnění požadavků nasazení technologií, jako [nasazení ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) nebo [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]vaší aplikace prohlížeče XAML technologie, která jim umožňují bezproblémové a zabezpečené nasazení aplikací klasické pracovní plochy z nedůvěryhodné weby.

## <a name="minimum-permission-requirements"></a>Požadavky na minimální oprávnění

WCF podporuje podmnožinu funkcí v aplikace spuštěné v některé z následujících sad standardní pojmenovaných oprávnění:

- Střední oprávnění důvěryhodnosti

- Oprávnění pro zónu Internetu

Pokus o použití WCF v částečně důvěryhodné aplikace s víc omezující oprávnění může vést k bezpečnostním výjimkám v době běhu.

Další informace o funkcích podporovaných v těchto sad oprávnění najdete v tématu [Kompatibilita funkce částečné důvěryhodnosti](partial-trust-feature-compatibility.md).

## <a name="partial-trust-on-the-server"></a>Částečné důvěryhodnosti na serveru

Mnoho poskytovatelů obchodní aplikace ASP.NET Web hostitelské služby stanoví, že aplikace spuštěné na jejich serverech běží v [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] úrovni Medium Trust sadu oprávnění. Služby WCF můžete spustit v těchto prostředích, pokud používají <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WebHttpBinding>, nebo <xref:System.ServiceModel.WSHttpBinding> se zabezpečením na úrovni přenosu.

WCF služby spuštěné na úrovni Medium Trust hostitelská prostředí se mohou chovat i jako střední vrstvy služby odesíláním zpráv na jiné servery v reakci na požadavky klientů. Střední vrstvy scénáře na serveru jsou podporovány, pokud hostitelské prostředí udělil aplikace odpovídající <xref:System.Net.WebPermission> provádět požadavky na odchozích k požadovanému serveru.

Kromě pomocí jedné z podporovaných vazby SOAP zasílání zpráv SOAP, podporuje WCF <xref:System.ServiceModel.WebHttpBinding> pro vytváření webových služeb v částečně důvěryhodné aplikace. [WCF Web HTTP programovací Model](wcf-web-http-programming-model.md), [syndikace WCF](wcf-syndication.md), a [integrace jazyka AJAX a podpora formátu JSON](ajax-integration-and-json-support.md) funkcí služby WCF je dostupná v částečném vztahu důvěryhodnosti.

Služby pracovních postupů, vyžadují oprávnění plné důvěryhodnosti a nelze použít v částečně důvěryhodné aplikace.

Další informace najdete v tématu [jak: Použití střední důvěryhodnosti v technologii ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=84603).

## <a name="partial-trust-on-the-client"></a>Částečné důvěryhodnosti na straně klienta

Při stahování a spouštění kódu z nedůvěryhodné weby na Internetu, musí být přijata určité bezpečnostní opatření. Obě [nasazení ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]XAML aplikace prohlížeče (XBAP) ujistěte se, technologie využití částečným vztahem důvěryhodnosti udělit omezená oprávnění (zóny Internet) nedůvěryhodného kódu.

WCF slouží ke komunikaci se vzdálenými servery z v rámci částečně důvěryhodné aplikace nasazené buď [nasazení ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) nebo XBAP. Zahrnuje sadu oprávnění zóny Internet <xref:System.Net.WebPermission> původního hostitele, který umožňuje tyto aplikace ke komunikaci s jejich zdrojový server pomocí kteréhokoli z podporovaných vazby WCF je popsáno v [Kompatibilita funkce částečné důvěryhodnosti ](partial-trust-feature-compatibility.md).

## <a name="see-also"></a>Viz také:

- [Zabezpečení přístupu kódu](../../misc/code-access-security.md)
- [Přehled Windows Presentation Foundation aplikace hostované prohlížečem](../../wpf/app-development/wpf-xaml-browser-applications-overview.md)
- [Částečná důvěryhodnost](partial-trust.md)
- [Úrovně důvěryhodnosti technologie ASP.NET a zásady souborů](https://docs.microsoft.com/previous-versions/wyts434y(v=vs.140))
