---
title: "Zabezpečení klientské aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 190e64945658f81400c2cc68beff82ccc38144f5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="secure-client-applications"></a>Zabezpečení klientské aplikace
Aplikace se obvykle skládají z mnoha částí, které musí všechny chráněné z chyb zabezpečení, které může dojít ke ztrátě dat nebo jinak ohrozit zabezpečení systému. Vytvoření zabezpečeného uživatelského rozhraní můžete zabránit mnoho problémů s blokováním útočníci před přístupem dat nebo dostatek systémových prostředků.  
  
## <a name="validate-user-input"></a>Ověření vstupu uživatele  
 Při vytváření aplikace, která přistupuje k datům, které by měl předpokládat, že všechny se zlými úmysly, dokud ověřené jinak vstup uživatele. Tak neučiníte nechte aplikaci bude zranitelný vůči útoku. Rozhraní .NET Framework obsahuje třídy, můžete vynutit domény hodnot pro vstupní ovládací prvky, jako je například omezení počtu znaků, které lze zadat. Háky událostí umožňují zápisu postup ověření hodnoty. Vstupní data uživatele může být ověřen a silného typu, omezení zneužití vystavení aplikace skriptu a Injektáž SQL.  
  
> [!IMPORTANT]
>  Musíte také ověřit uživatelský vstup ve zdroji dat a jako klientské aplikace. Útočník může rozhodnout obejít vaší aplikace a útokům zdroje dat přímo.  
  
 [Zabezpečení a uživatelský vstup](../../../../docs/standard/security/security-and-user-input.md)  
 Popisuje způsob zpracování chyb jemně a potenciálně nebezpečná zahrnující vstup uživatele.  
  
 [Ověřování uživatelského vstupu ve webových stránkách ASP.NET](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)  
 Přehled ověřování vstup uživatele s použitím ovládacích prvků ověřování ASP.NET.  
  
 [Uživatelský vstup ve Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 Obsahuje odkazy a informace o ověřování myši a v aplikaci Windows Forms vstup z klávesnice.  
  
 [Regulární výrazy rozhraní .NET framework](../../../../docs/standard/base-types/regular-expressions.md)  
 Popisuje postup použití <xref:System.Text.RegularExpressions.Regex> třída ověření vstupu uživatele.  
  
## <a name="windows-applications"></a>Aplikace systému Windows  
 V minulosti s úplnými oprávněními obecně spustili aplikace systému Windows. Rozhraní .NET Framework poskytuje infrastrukturu omezit spuštění kódu v aplikaci Windows pomocí zabezpečení přístupu kódu (CAS). Samostatné certifikační Autority je však není dostatek k ochraně vaší aplikace.  
  
 [Windows Forms – zabezpečení](../../../../docs/framework/winforms/windows-forms-security.md)  
 Popisuje, jak zabezpečit aplikace Windows Forms a poskytuje odkazy na související témata.  
  
 [Model Windows Forms a nespravované aplikace](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Popisuje, jak pracovat s nespravovaných aplikací v aplikaci Windows Forms.  
  
 [Aplikace ClickOnce – nasazení pro systém Windows Forms](http://msdn.microsoft.com/en-us/34d8c770-48f2-460c-8d67-4ea5684511df)  
 Popisuje způsob použití `ClickOnce` nasazení v aplikaci Windows Forms a popisuje bezpečnostní důsledky.  
  
## <a name="aspnet-and-xml-web-services"></a>Technologie ASP.NET a webové služby XML  
 Aplikace ASP.NET obecně nutné omezit přístup k některé části webu a poskytují další mechanismy pro ochranu dat a zabezpečení lokality. Tyto odkazy poskytují užitečné informace pro zabezpečení aplikace ASP.NET.  
  
 Webové služby XML obsahuje data, která mohou být spotřebovávána aplikace ASP.NET, formulářové aplikace Windows nebo jiné webové služby. Budete muset spravovat zabezpečení pro webovou službu, samotné, jakož i zabezpečení pro klientské aplikace.  
  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[NIB: Zabezpečení ASP.NET](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d)|Popisuje, jak zabezpečit aplikace ASP.NET.|  
|[Zabezpečení webové služby XML vytvořených pomocí technologie ASP.NET](http://msdn.microsoft.com/en-us/354b2ab1-2782-4542-b32a-dc560178b90c)|Popisuje, jak implementovat zabezpečení pro webové služby ASP.NET.|  
|[Přehled zneužití skriptu](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|Popisuje, jak chránit proti útoku zneužití skriptu, která se pokusí vložit škodlivý znaků do webové stránky.|  
|[NIB: základní postupy zabezpečení pro webové aplikace ASP.NET](http://msdn.microsoft.com/en-us/94a52ab8-731d-417e-b997-721baf43df38)|Obecné informace zabezpečení a odkazy na další informace|  
  
## <a name="remoting"></a>Vzdálená komunikace  
 .NET remoting umožňuje snadno vytvořit široce distribuované aplikace zda součástí aplikace jsou všechny v jednom počítači nebo rozloženy celého světa. Můžete vytvořit klienta aplikace, které používají objekty v jiných procesech na stejném počítači nebo na jiný počítač, který je dosažitelný prostřednictvím své sítě. Můžete taky .NET remoting ke komunikaci s ostatními doménami aplikací v rámci jednoho procesu.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Konfigurace vzdálené aplikace](http://msdn.microsoft.com/en-us/92c0c097-d984-4315-835b-7490ecdf1097)|Popisuje postup konfigurace aplikací vzdálené komunikace, aby se zabránilo běžné problémy.|  
|[Zabezpečení vzdálené komunikace](http://msdn.microsoft.com/en-us/9574262c-d4b1-41c5-8600-24ff147c0add)|Popisuje ověřování a šifrování, jakož i další bezpečnostní témata, které jsou relevantní pro vzdálenou komunikaci.|  
|[Zabezpečení a důležité informace o vzdálené komunikace](../../../../docs/framework/misc/security-and-remoting-considerations.md)|Popisuje problémy se zabezpečením s chráněných objektech a překročení domény aplikace.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Doporučení pro strategií přístupu dat](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Zabezpečování aplikací](/visualstudio/ide/securing-applications)  
 [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
