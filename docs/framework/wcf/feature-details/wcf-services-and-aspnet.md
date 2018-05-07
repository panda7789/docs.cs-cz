---
title: Služby WCF a ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 6cfd4f8a5dc2a7835cba409a37b09166e49e8df3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-services-and-aspnet"></a>Služby WCF a ASP.NET
Toto téma popisuje hostování Windows Communication Foundation (WCF) služby-souběžného s ASP.NET a jejich hostování v režimu kompatibility ASP.NET.  
  
## <a name="hosting-wcf-side-by-side-with-aspnet"></a>Hostování WCF-souběžného s technologií ASP.NET  
 Služby WCF hostované v Internetové informační služby (IIS) můžou být s. Stránky ASPX a ASMX webové služby v rámci jedné, běžné domény aplikace. Technologie ASP.NET poskytuje obecné služby infrastruktury, jako je Správa AppDomain a dynamická kompilace pro WCF a ASP.NET HTTP runtime. Výchozí konfiguraci pro WCF je vedle sebe s technologií ASP.NET.  
  
 ![Služby WCF a rozhraní ASP .NET: sdílení stavu](../../../../docs/framework/wcf/feature-details/media/hostingwcfwithaspnet.gif "HostingWCFwithASPNET")  
  
 Modul runtime ASP.NET HTTP zpracovává požadavky ASP.NET ale neúčastní zpracování požadavků určených pro služby WCF, i když tyto služby jsou hostované do stejné domény aplikace, jako je ASP.NET obsahu. Místo toho modelu služby WCF zachycuje zprávy adresované do služby WCF a směruje je přes protokolů přenosu/kanál WCF.  
  
 Výsledky vedle sebe modelu jsou následující:  
  
-   Technologie ASP.NET a WCF services můžete sdílet AppDomain stavu. Vzhledem k tomu, že dvě rozhraní můžou existovat společně, do stejné domény aplikace, WCF můžou taky sdílet stavu AppDomain s technologií ASP.NET (včetně statické proměnné, události a tak dále).  
  
-   Služby WCF chovat konzistentně, nezávisle na hostování prostředí a přenosu. Modul runtime ASP.NET HTTP je záměrně vázány na IIS/ASP.NET hostování prostředí a komunikaci pomocí protokolu HTTP. Naopak WCF umožňuje chovat konzistentně napříč hostitelská prostředí (WCF chová konzistentně obě uvnitř i vně služby IIS) a přes přenosu (služby hostované ve službě IIS 7.0 nebo novější je konzistentní chování napříč všechny koncové body, které vystavuje, i když Některé z těchto koncových bodů použít jiné protokoly než HTTP).  
  
-   V objektu AppDomain použít funkce implementované HTTP runtime ASP.NET obsah, ale nechcete WCF. Mnoho funkcí specifické platformy aplikace ASP.NET se nevztahují na služby WCF hostované v objektu AppDomain, který obsahuje obsahu ASP.NET. Mezi tyto funkce patří:  
  
    -   Položka HttpContext: <xref:System.Web.HttpContext.Current%2A> je vždy `null` přistupováno z v rámci služby WCF. Použití <!--zz <xref:System.ServiceModel.OperationContext.Current.RequestContext>--> `RequestContext` místo.  
  
    -   Na základě souborů autorizace: model zabezpečení WCF nepovoluje seznamu řízení přístupu (ACL) u souboru .svc služby při rozhodování, jestli je autorizovaný žádost o služby.  
  
    -   Autorizace adres URL na základě konfigurace: Podobně modelu zabezpečení WCF nedrží všechna pravidla autorizace na základě adresy URL zadané v System.Web na \<autorizace > konfigurační prvek. Tato nastavení ignorují požadavkům WCF, pokud se služba nachází v prostoru adresy URL zabezpečeny ASP. NET na autorizačních pravidel adres URL.  
  
    -   Rozšíření modulu http: WCF hostování infrastruktury zachytí WCF požadavky, když <xref:System.Web.HttpApplication.PostAuthenticateRequest> nevrací zpracování kanálu ASP.NET protokolu HTTP a je vyvolána událost. Moduly, které jsou programového za účelem zachycení požadavků na novější fázemi kanálu není zachycení požadavků WCF.  
  
    -   Zosobnění technologie ASP.NET: ve výchozím nastavení, WCF požadavků vždy běží jako služba IIS zpracovávat identitu, i v případě, že technologie ASP.NET je nastavit pro povolení zosobnění pomocí na System.Web \<zosobnit identitu = "true" / > Možnosti konfigurace.  
  
 Tato omezení platí pouze pro služby WCF hostované v aplikaci služby IIS. Chování obsahu ASP.NET nemá vliv na přítomnost WCF.  
  
 Aplikace WCF, které vyžadují funkce tradičně poskytované službou kanál protokolu HTTP měli zvážit použití ekvivalenty WCF, které jsou hostiteli a přenosu nezávislé:  
  
-   <xref:System.ServiceModel.OperationContext> místo <xref:System.Web.HttpContext>.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> místo ASP. NET na soubor nebo adresa URL autorizace.  
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> nebo vlastní vrstveného kanály místo vytváření modulů HTTP.  
  
-   Zosobnění pro každou operaci pomocí WCF místo System.Web zosobnění.  
  
 Alternativně můžete zvážit službami v režimu kompatibility ASP.NET na WCF.  
  
## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>Hostování služby WCF v režimu kompatibility ASP.NET  
 Přestože modelu WCF je navržený chovat konzistentně napříč hostitelských prostředích a přenosy, jsou často scénáře, kde aplikace nevyžaduje takové pružnosti. Režim kompatibility ASP.NET na WCF je vhodná pro scénáře, který nevyžaduje možnost hostitel mimo služby IIS nebo pro komunikaci pomocí jiné protokoly než HTTP, ale který používat všechny funkce na platformě ASP.NET – webové aplikace.  
  
 Na rozdíl od výchozí souběžně sdílená konfigurace, kde infrastruktury hostování WCF zachycuje zpráv WCF a směruje je mimo kanál protokolu HTTP, služby WCF, které běží v režimu kompatibility ASP.NET účastnit plně životního cyklu požadavku HTTP technologie ASP.NET. V režimu kompatibility, služby WCF použití kanálu HTTP prostřednictvím <xref:System.Web.IHttpHandler> implementace, podobně jako na požadavky na způsob pro stránky ASPX a ASMX webových služeb jsou zpracovávány. V důsledku toho WCF se chová stejně ASMX s ohledem na tyto funkce ASP.NET:  
  
-   <xref:System.Web.HttpContext>: Služby WCF spuštěné v režimu kompatibility ASP.NET můžete k <xref:System.Web.HttpContext.Current%2A> a jeho přidružený stav.  
  
-   Na základě souborů autorizace: WCF služby spuštěné v režimu kompatibility ASP.NET může být zabezpečené pomocí souborového systému seznamy řízení přístupu (ACL) se připojuje k souboru .svc služby.  
  
-   Konfigurovat autorizace adres URL: ASP. Při služba WCF běží v režimu kompatibility ASP.NET autorizačních pravidel adres URL na NET prosazují požadavkům WCF.  
  
-   <xref:System.Web.HttpModuleCollection> rozšiřitelnost: protože WCF služby spuštěné v režimu kompatibility ASP.NET plně účastnit v životním cyklu požadavku HTTP technologie ASP.NET, je možné pracovat WCF požadavky před a po volání služby libovolný modul HTTP nakonfigurované v kanálu HTTP.  
  
-   Zosobnění technologie ASP.NET: Služby WCF spouštět s využitím aktuální identitu ASP.NET zosobnit podproces, který může být jiný než identitě procesu služby IIS, pokud bylo povoleno zosobnění technologie ASP.NET pro aplikaci. Pokud zosobnění technologie ASP.NET a WCF zosobnění jsou povolené pro konkrétní službu operaci, spustí implementace služby nakonec pomocí identity získané z WCF.  
  
 Režim kompatibility ASP.NET na WCF je povolena na úrovni aplikace pomocí následující konfigurace (nachází se v souboru Web.config aplikace):  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />  
</system.serviceModel>  
```  
  
 Výchozí hodnota je "`true`" Pokud není zadaný. Nastavení této hodnoty na "`false`" označuje, že všechny služby WCF, které jsou spuštěné v aplikaci nebude spuštěn v režimu kompatibility ASP.NET.  
  
 Protože režim kompatibility ASP.NET znamená sémantiku zpracování požadavku, která se zásadně liší od výchozí WCF, implementací jednotlivé služby zda poběží v rámci aplikace ASP.NET, které mít možnost ovládací prvek Režim kompatibility byla povolena. Služby, můžou používat <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> indikující, zda podporují režim kompatibility ASP.NET. Výchozí hodnota pro tento atribut je <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.  
  
 `[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]`  
  
 `public class CalculatorService : ICalculatorSession`  
  
 `{//Implement calculator service methods.}`  
  
 Následující tabulka vysvětluje, jak nastavení režim kompatibility celé aplikace komunikuje s jednotlivé služby stanovené úroveň podpory:  
  
|Nastavení režimu kompatibility celé aplikace|[AspNetCompatibilityRequirementsMode]<br /><br /> Nastavení|Pozorovaných výsledků|  
|--------------------------------------------------|---------------------------------------------------------|---------------------|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Služba aktivuje úspěšně.|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Služba aktivuje úspěšně.|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Když služba obdrží zprávu dojde k chybě aktivace.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Když služba obdrží zprávu dojde k chybě aktivace.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Služba aktivuje úspěšně.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Služba aktivuje úspěšně.|  
  
> [!NOTE]
>  IIS 7.0 a WAS umožňuje službám WCF pro komunikaci pomocí jiné protokoly než HTTP. Služby WCF, které jsou spuštěné v aplikacích, které jste povolili režim kompatibility ASP.NET však nejsou povoleny vystavit koncové body jiným protokolem než HTTP. Taková konfigurace generuje výjimku aktivace, když služba přijme jeho první zprávy.  
  
 Další informace o povolení režim kompatibility ASP.NET pro služby WCF najdete v tématu <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> a [režim kompatibility ASP.NET](../../../../docs/framework/wcf/samples/aspnet-compatibility.md) ukázka.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
