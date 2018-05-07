---
title: Podporované scénáře nasazení
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: d0afd12b1c17f9356146aa13c90f8db65ed9ec0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="supported-deployment-scenarios"></a>Podporované scénáře nasazení
Do něj podmnožinu funkcí Windows Communication Foundation (WCF) podporovaných pro použití v částečně důvěryhodné aplikace je navržená ke splnění požadavků některé, ale ne všechny scénáře použití WCF. Na serveru, sdíleného WCF splňuje požadavky na internetových poskytovatelé hostitelských služeb, kteří používají aplikace třetích stran v [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] oprávnění na úrovni Medium Trust nastavit z bezpečnostních důvodů. Na straně klienta WCF částečnou důvěryhodností podporu slouží ke splnění požadavků nasazení technologie, jako [ClickOnce – nasazení](http://go.microsoft.com/fwlink/?LinkId=83712) nebo [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]na aplikace prohlížeče XAML technologii, která umožňují hladkou a zabezpečenou nasazení aplikací klasické pracovní plochy umístěné na serverech.  
  
## <a name="minimum-permission-requirements"></a>Požadavky na minimální oprávnění  
 WCF podporuje podmnožinu funkcí v aplikacích spuštěných v některé z následujících sad standardní pojmenované oprávnění:  
  
-   Střední oprávnění vztahu důvěryhodnosti  
  
-   Oprávnění pro zónu Internetu  
  
 Pokus o použití WCF v částečně důvěryhodné aplikace s víc omezující oprávnění může vést k bezpečnostním výjimkám za běhu.  
  
 Další informace o funkcích podporovaných v těchto sady oprávnění najdete v tématu [Kompatibilita funkcí s částečnou důvěřovat](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="partial-trust-on-the-server"></a>Částečná důvěryhodnost na serveru  
 Mnoho poskytovatelů komerční z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hostování webových aplikací služby pověření, které aplikace běžící na jejich serverech spustit v [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] úrovni Medium Trust sadu oprávnění. Služby WCF, které mohou být spuštěny v těchto prostředích se používají <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WebHttpBinding>, nebo <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> s zabezpečení na úrovni přenosu.  
  
 Služby WCF, které jsou spuštěné na úrovni Medium Trust hostitelská prostředí mohou chovat i jako střední vrstvy služby pomocí odesílání zpráv na jiné servery v reakci na požadavky klientů. Jsou podporované scénáře střední vrstvy na serveru, pokud hostitelské prostředí přidělili aplikace odpovídající <xref:System.Net.WebPermission> provádět odchozí požadavky k požadovanému serveru.  
  
 Kromě zasílání zpráv protokolu SOAP s jedním z podporovaných vazby protokolu SOAP a podporuje WCF <xref:System.ServiceModel.WebHttpBinding> pro vytváření stylu webových služeb v částečně důvěryhodné aplikace. [WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md), [syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md), a [integrace jazyka AJAX a podpora formátu JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md) všechny funkce služby WCF jsou podporovány v částečné důvěryhodnosti.  
  
 Pracovní postup služby vyžadují oprávnění úplné důvěryhodnosti a nelze použít v částečně důvěryhodné aplikace.  
  
 Další informace najdete v tématu [postupy: použití střední důvěryhodnosti v technologii ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=84603).  
  
## <a name="partial-trust-on-the-client"></a>Částečná důvěryhodnost na straně klienta  
 Určitá bezpečnostní opatření musí být provedeny, když stahování a spouštění kódu z nedůvěryhodné internetových serverů. Obě [ClickOnce – nasazení](http://go.microsoft.com/fwlink/?LinkId=83712) a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]aplikace prohlížeče XAML (XBAP) ujistěte se, technologie využití částečnou důvěryhodností udělit omezenými oprávněními (zónu Internetu) do nedůvěryhodného kódu.  
  
 WCF lze použít ke komunikaci s vzdálených serverů z v rámci částečně důvěryhodné aplikace nasazené buď [ClickOnce – nasazení](http://go.microsoft.com/fwlink/?LinkId=83712) nebo XBAP. Zahrnuje sadu oprávnění zónu Internetu <xref:System.Net.WebPermission> pro původní hostitele, který umožňuje tyto aplikace ke komunikaci s jejich původním serveru pomocí některé z podporovaných vazby WCF, které jsou popsané v [Kompatibilita funkcí s částečné důvěryhodnosti ](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení přístupu kódu](http://go.microsoft.com/fwlink/?LinkId=83717)  
 [Windows Presentation Foundation – přehled – aplikace hostované prohlížečem](http://go.microsoft.com/fwlink/?LinkId=98397)  
 [Částečná důvěryhodnost](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 [Střední ASP.Net důvěryhodnosti](http://go.microsoft.com/fwlink/?LinkId=69328)
