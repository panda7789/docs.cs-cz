---
title: "Podporované scénáře nasazení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 22dcace51b2c73193356450b4b210d1c1a899e28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="supported-deployment-scenarios"></a>Podporované scénáře nasazení
Podmnožinu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkcí podporovaných pro použití v částečně důvěryhodné aplikace slouží ke splnění požadavků některé, ale ne všechny scénáře použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Na serveru [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] splňuje požadavky na internetových sdílené poskytovatelé hostitelských služeb, kteří používají aplikace třetích stran v [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] oprávnění na úrovni Medium Trust nastavit z bezpečnostních důvodů. Na straně klienta [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporu částečné důvěryhodnosti je tak, aby splnily požadavky na nasazení technologie, jako [ClickOnce – nasazení](http://go.microsoft.com/fwlink/?LinkId=83712) nebo [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]na aplikace prohlížeče XAML technologii, která umožňují plynulé a bezpečné nasazení aplikací klasické pracovní plochy umístěné na serverech.  
  
## <a name="minimum-permission-requirements"></a>Požadavky na minimální oprávnění  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje podmnožinu funkcí v aplikacích spuštěných v některé z následujících sad standardní pojmenované oprávnění:  
  
-   Střední oprávnění vztahu důvěryhodnosti  
  
-   Oprávnění pro zónu Internetu  
  
 Pokus o použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] v částečně důvěryhodné aplikace s víc omezující oprávnění, které může vést k bezpečnostním výjimkám za běhu.  
  
 Další informace o funkcích podporovaných v těchto sady oprávnění najdete v tématu [Kompatibilita funkcí s částečnou důvěřovat](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="partial-trust-on-the-server"></a>Částečná důvěryhodnost na serveru  
 Mnoho poskytovatelů komerční z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hostování webových aplikací služby pověření, které aplikace běžící na jejich serverech spustit v [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] úrovni Medium Trust sadu oprávnění. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby, které mohou být spuštěny v těchto prostředích se používají <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WebHttpBinding>, nebo <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> s zabezpečení na úrovni přenosu.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby spuštěné na úrovni Medium Trust hostitelská prostředí mohou chovat i jako střední vrstvy služby pomocí odesílání zpráv na jiné servery v reakci na požadavky klientů. Jsou podporované scénáře střední vrstvy na serveru, pokud hostitelské prostředí přidělili aplikace odpovídající <xref:System.Net.WebPermission> provádět odchozí požadavky k požadovanému serveru.  
  
 Kromě SOAP zasílání zpráv pomocí jedné z podporovaných vazby protokolu SOAP, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje <xref:System.ServiceModel.WebHttpBinding> pro vytváření stylu webových služeb v částečně důvěryhodné aplikace. [WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md), [syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md), a [integrace jazyka AJAX a podpora formátu JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md) funkce [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou podporovány v částečné důvěryhodnosti.  
  
 Pracovní postup služby vyžadují oprávnění úplné důvěryhodnosti a nelze použít v částečně důvěryhodné aplikace.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Postupy: použití střední důvěryhodnosti v technologii ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=84603).  
  
## <a name="partial-trust-on-the-client"></a>Částečná důvěryhodnost na straně klienta  
 Určitá bezpečnostní opatření musí být provedeny, když stahování a spouštění kódu z nedůvěryhodné internetových serverů. Obě [ClickOnce – nasazení](http://go.microsoft.com/fwlink/?LinkId=83712) a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]aplikace prohlížeče XAML (XBAP) ujistěte se, technologie využití částečnou důvěryhodností udělit omezenými oprávněními (zónu Internetu) do nedůvěryhodného kódu.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]slouží ke komunikaci s vzdálených serverů z v rámci částečně důvěryhodné aplikace nasazené buď [ClickOnce – nasazení](http://go.microsoft.com/fwlink/?LinkId=83712) nebo XBAP. Zahrnuje sadu oprávnění zónu Internetu <xref:System.Net.WebPermission> pro původní hostitele, který umožňuje tyto aplikace ke komunikaci s jejich původním serveru pomocí kteréhokoli podporovaném [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby popsané v [funkce částečné důvěryhodnosti Kompatibilita](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení přístupu kódu](http://go.microsoft.com/fwlink/?LinkId=83717)  
 [Windows Presentation Foundation – přehled – aplikace hostované prohlížečem](http://go.microsoft.com/fwlink/?LinkId=98397)  
 [Částečná důvěryhodnost](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 [Střední ASP.Net důvěryhodnosti](http://go.microsoft.com/fwlink/?LinkId=69328)
