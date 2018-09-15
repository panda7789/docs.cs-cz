---
title: Zabezpečené klientské aplikace
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: a3b035d59a39ca20f6a81fbd40d39069a7cc43c2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649169"
---
# <a name="secure-client-applications"></a>Zabezpečené klientské aplikace
Aplikace se obvykle skládají z mnoho částí, které musí ochránit před chybami zabezpečení, které by mohly způsobit ztrátu dat nebo jinak ohrozit zabezpečení systému. Vytváření zabezpečených uživatelské rozhraní může zabránit mnoho problémů zákonné zodpovědnosti organizací blokováním útočníci před získáním přístupu dat nebo dostatek systémových prostředků.  
  
## <a name="validate-user-input"></a>Ověření vstupu uživatele  
 Při vytváření aplikace, která přistupuje k datům, byste měli předpokládat, který všechny zadání uživatele se zlými úmysly, dokud prověřené na jinak. Pokud tak neučiníte nechte aplikaci snadno napadnutelný. Rozhraní .NET Framework obsahuje třídy, které pomáhají vynutit domény hodnot pro vstupní ovládací prvky, jako je například omezení počtu znaků, které může uživatel zadat. Háky událostí umožňuje psát postupy ověření hodnoty. Vstupní data uživatele může být ověřen a silného typu, omezení zneužije aplikace ohrožení skript a útok prostřednictvím injektáže SQL.  
  
> [!IMPORTANT]
>  Musíte také ověřit uživatelský vstup ve zdroji dat stejně jako v klientské aplikaci. Útočník může rozhodnout obejít vaší aplikace a zdroj dat přímo útoku.  
  
 [Zabezpečení a uživatelský vstup](../../../../docs/standard/security/security-and-user-input.md)  
 Popisuje způsob zpracování chyb potenciálně nebezpečné a současně lákavé zahrnující vstup uživatele.  
  
 [Ověřování uživatelského vstupu v ASP.NET Web Pages](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)  
 Přehled ověřování vstupu uživatele s použitím validačních ovládacích prvků technologie ASP.NET.  
  
 [Uživatelský vstup ve Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 Poskytuje odkazy a informace pro ověřování myši a klávesnice v aplikaci Windows Forms.  
  
 [Regulárních výrazech .NET Frameworku](../../../../docs/standard/base-types/regular-expressions.md)  
 Popisuje způsob použití <xref:System.Text.RegularExpressions.Regex> třídy ověření vstupu uživatele.  
  
## <a name="windows-applications"></a>Aplikace Windows  
 V minulosti Windows byla aplikace obecně spuštěna s úplnými oprávněními. Rozhraní .NET Framework poskytuje infrastrukturu pro omezení spuštění kódu v aplikaci s Windows pomocí zabezpečení přístupu kódu (CAS). Ale certifikačních Autorit samostatně nestačí k ochraně vaší aplikace.  
  
 [Windows Forms – zabezpečení](../../../../docs/framework/winforms/windows-forms-security.md)  
 Popisuje, jak zabezpečit aplikace Windows Forms a obsahuje odkazy na související témata.  
  
 [Model Windows Forms a nespravované aplikace](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Popisuje, jak pracovat s nespravovanými aplikacemi v aplikaci Windows Forms.  
  
 [ClickOnce – nasazení pro Windows Forms aplikací](https://msdn.microsoft.com/library/34d8c770-48f2-460c-8d67-4ea5684511df)  
 Popisuje způsob použití `ClickOnce` nasazení v aplikaci Windows Forms a probírá důsledky zabezpečení.  
  
## <a name="aspnet-and-xml-web-services"></a>ASP.NET a webových služeb XML  
 Aplikace ASP.NET obecně nutné omezit přístup k některé části webu a poskytují další mechanismy pro ochranu dat a zabezpečení serveru. Tyto odkazy poskytují užitečné informace pro zabezpečení aplikace ASP.NET.  
  
 Webové služby XML obsahuje data, která mohou být spotřebovány aplikaci ASP.NET, aplikace modelu Windows Forms nebo jiné webové služby. Potřebujete spravovat zabezpečení pro samotnou webovou službu, jakož i zabezpečení pro klientské aplikace.  
  
 Další informace najdete v tématu následující prostředky.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[NIB: Zabezpečení technologie ASP.NET](https://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d)|Popisuje, jak zabezpečené aplikace ASP.NET.|  
|[Zabezpečení webových služeb XML vytvořených pomocí technologie ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c)|Popisuje, jak implementovat zabezpečení pro webovou službu ASP.NET.|  
|[Přehled zneužití skriptu](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|Popisuje, jak pro ochranu proti útoku zneužití skriptu, která se pokusí vložit škodlivé znaky do webové stránky.|  
|[NIB: základní postupy zabezpečení pro webové aplikace ASP.NET](https://msdn.microsoft.com/library/94a52ab8-731d-417e-b997-721baf43df38)|Obecné informace zabezpečení a odkazy na další informace|  
  
## <a name="remoting"></a>Vzdálená komunikace  
 Vzdálené komunikace .NET vám umožní sestavovat široce distribuovaných aplikací, ať už součástí aplikace jsou všechny na jednom počítači nebo rozloženy na světě. Můžete vytvořit klientské aplikace, které používají objekty v jiných procesů ve stejném počítači nebo na jiný počítač, který je dostupný prostřednictvím své sítě. Vzdálené komunikace .NET můžete použít také ke komunikaci s dalšími doménami aplikace v rámci stejného procesu.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Konfigurace vzdálené aplikace](https://msdn.microsoft.com/library/92c0c097-d984-4315-835b-7490ecdf1097)|Tento článek popisuje postup konfigurace aplikací vzdálené komunikace, aby se zabránilo běžné problémy.|  
|[Zabezpečení vzdálené komunikace](https://msdn.microsoft.com/library/9574262c-d4b1-41c5-8600-24ff147c0add)|Popisuje, ověřování a šifrování, jakož i další bezpečnostní témata, které jsou relevantní pro vzdálenou komunikaci.|  
|[Zabezpečení a důležité informace o vzdálené komunikace](../../../../docs/framework/misc/security-and-remoting-considerations.md)|Popisuje problémy se zabezpečením pomocí chráněných objektů a křížení domén aplikace.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Doporučení pro strategií přístupu dat](https://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Zabezpečování aplikací](/visualstudio/ide/securing-applications)  
 [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
