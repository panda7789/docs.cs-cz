---
title: Zabezpečené klientské aplikace
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: 15d2b2199344644392be0e9a530c046a77db8523
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794381"
---
# <a name="secure-client-applications"></a>Zabezpečené klientské aplikace
Aplikace se obvykle skládají z mnoha částí, které musí být chráněné před chybami zabezpečení, které by mohly vést ke ztrátě dat nebo jinak ohrozit systém. Vytváření zabezpečených uživatelských rozhraní může zabránit mnoha problémům tím, že by útočník mohl získat přístup k datovým nebo systémovým prostředkům.  
  
## <a name="validate-user-input"></a>Ověřit vstup uživatele  
 Při sestavování aplikace, která přistupuje k datům, byste měli předpokládat, že veškerý vstup uživatele je škodlivý, dokud nebude prověřen jinak. V takovém případě může aplikace způsobit zranitelnost vůči útokům. .NET Framework obsahuje třídy, které vám pomůžou vyhodnotit doménu hodnot pro vstupní ovládací prvky, jako je například omezení počtu znaků, které lze zadat. Zavěšení událostí umožňují napsat postupy pro kontrolu platnosti hodnot. Data uživatelského vstupu můžou být ověřená a silně typu, což omezuje expozici aplikace pro skripty a zneužití injektáže SQL.  
  
> [!IMPORTANT]
> Také je nutné ověřit vstup uživatele ve zdroji dat i v klientské aplikaci. Útočník se může rozhodnout pro obejít vaší aplikaci a útok přímo na zdroj dat.  
  
 [Zabezpečení a uživatelský vstup](../../../standard/security/security-and-user-input.md)  
 Popisuje způsob zpracování drobných a potenciálně nebezpečných chyb týkajících se vstupu uživatele.  
  
 [Ověřování vstupu uživatele na webových stránkách ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/7kh55542(v=vs.100))  
 Přehled ověřování vstupu uživatele pomocí ovládacích prvků ověřování ASP.NET  
  
 [Uživatelský vstup ve Windows Forms](../../winforms/user-input-in-windows-forms.md)  
 Poskytuje odkazy a informace pro ověřování vstupu myši a klávesnice v aplikaci model Windows Forms.  
  
 [.NET Framework regulární výrazy](../../../standard/base-types/regular-expressions.md)  
 Popisuje, jak použít <xref:System.Text.RegularExpressions.Regex> třídu ke kontrole platnosti vstupu uživatele.  
  
## <a name="windows-applications"></a>Aplikace systému Windows  
 V minulosti aplikace systému Windows obecně běžely s úplnými oprávněními. .NET Framework poskytuje infrastrukturu k omezení spouštění kódu v aplikaci systému Windows pomocí zabezpečení přístupu kódu (CAS). Pouze CAS ale nestačí k ochraně vaší aplikace.  
  
 [Windows Forms – zabezpečení](../../winforms/windows-forms-security.md)  
 Popisuje, jak zabezpečit aplikace model Windows Forms a obsahuje odkazy na související témata.  
  
 [Model Windows Forms a nespravované aplikace](../../winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Popisuje, jak pracovat s nespravovanými aplikacemi v aplikaci model Windows Forms.  
  
 [ClickOnce – nasazení pro Windows Forms](../../winforms/clickonce-deployment-for-windows-forms.md)  
 Popisuje, jak použít `ClickOnce` nasazení v aplikaci model Windows Forms a popisuje dopady na zabezpečení.  
  
## <a name="aspnet-and-xml-web-services"></a>Webové služby ASP.NET a XML  
 ASP.NET aplikace obecně potřebují omezit přístup na některé části webu a zajistit další mechanismy ochrany dat a zabezpečení lokality. Tyto odkazy poskytují užitečné informace pro zabezpečení aplikace v ASP.NET.  
  
 Webová služba XML poskytuje data, která lze spotřebovat pomocí aplikace ASP.NET, aplikace model Windows Forms nebo jiné webové služby. Musíte spravovat zabezpečení samotné webové služby a také zabezpečení pro klientskou aplikaci.  
  
 Další informace najdete v následujících materiálech.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Zabezpečení webů ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100))|Popisuje, jak zabezpečit aplikace ASP.NET.|  
|[Zabezpečení webových služeb XML vytvořených pomocí ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))|Popisuje, jak implementovat zabezpečení webové služby ASP.NET.|  
|[Přehled zneužití skriptů](https://docs.microsoft.com/previous-versions/aspnet/w1sw53ds(v=vs.100))|Tento článek popisuje, jak chránit před útokem na zneužití skriptu, který se pokouší vložit škodlivé znaky do webové stránky.|  
|[Základní postupy zabezpečení pro webové aplikace](https://docs.microsoft.com/previous-versions/aspnet/zdh19h94(v=vs.100))|Obecné informace o zabezpečení a odkazy na další diskuzi,|  
  
## <a name="remoting"></a>Vzdálenou  
 Vzdálená komunikace .NET umožňuje snadno vytvářet rozsáhlé distribuované aplikace, ať už jsou komponenty aplikace všechny na jednom počítači nebo rozloženy po celém světě. Můžete vytvářet klientské aplikace, které používají objekty v jiných procesech ve stejném počítači nebo v jakémkoli jiném počítači, který je dosažitelný v rámci své sítě. Můžete také použít vzdálenou komunikaci rozhraní .NET ke komunikaci s ostatními aplikačními doménami ve stejném procesu.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Konfigurace vzdálených aplikací](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b8tysty8(v=vs.100))|Tento článek popisuje, jak nakonfigurovat vzdálené aplikace, aby se předešlo běžným problémům.|  
|[Zabezpečení při vzdálené komunikaci](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9hwst9th(v=vs.100))|Popisuje ověřování a šifrování a další témata zabezpečení týkající se vzdálené komunikace.|  
|[Problematika zabezpečení a vzdálené komunikace](../../misc/security-and-remoting-considerations.md)|Popisuje problémy se zabezpečením chráněných objektů a křížení domény aplikace.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](securing-ado-net-applications.md)
- [Doporučení pro strategie přístupu k datům](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))
- [Zabezpečování aplikací](/visualstudio/ide/securing-applications)
- [Ochrana informací o připojení](protecting-connection-information.md)
- [Přehled ADO.NET](ado-net-overview.md)
