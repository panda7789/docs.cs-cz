---
title: Služby WCF a ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 58b5a09f63b6efb3c48fb3836da63c24650c5b21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712282"
---
# <a name="wcf-services-and-aspnet"></a>Služby WCF a ASP.NET
Toto téma popisuje hostování Windows Communication Foundation (WCF) služby-souběžně s technologií ASP.NET a hostování v režim kompatibility ASP.NET.  
  
## <a name="hosting-wcf-side-by-side-with-aspnet"></a>Hostování WCF – souběžně s rozhraním ASP.NET  
 Služby WCF hostované v Internetové informační služby (IIS) mohou být umístěny s. Stránky ASPX a ASMX webovými službami v rámci jednoho, běžné domény aplikace. Technologie ASP.NET poskytuje běžné služby infrastruktury, jako je Správa domény aplikace a dynamická kompilace pro WCF a ASP.NET HTTP runtime. Výchozí konfigurace pro službu WCF je vedle sebe s technologií ASP.NET.  
  
 ![Služby WCF a ASP .NET: sdílení stavu](../../../../docs/framework/wcf/feature-details/media/hostingwcfwithaspnet.gif "HostingWCFwithASPNET")  
  
 Modul runtime ASP.NET HTTP zpracovává požadavky ASP.NET, ale není součástí zpracování požadavků určených pro služby WCF, i když tyto služby jsou hostované v téže doméně AppDomain, jako je ASP.NET obsahu. Místo toho modelu služby WCF zachycuje zprávy adresované do služby WCF a směruje je do zásobníku/kanál přenosu WCF.  
  
 Výsledky vedle sebe modelu jsou následující:  
  
-   ASP.NET a WCF služby můžou sdílet stavu domény aplikace. Protože dvou platforem mohou existovat vedle sebe v téže doméně AppDomain, WCF můžete také sdílet stavu domény aplikace s ASP.NET (včetně statických proměnných, události a tak dále).  
  
-   Služby WCF se chovají, nezávisle na hostování prostředí a přenosu. Modul runtime ASP.NET HTTP je záměrně spjat s IIS/ASP.NET hostování prostředí a komunikaci pomocí protokolu HTTP. Naopak WCF slouží chovat konzistentně napříč hostitelská prostředí (WCF chová konzistentně obě uvnitř i vně služby IIS) a mezi přenosu (služby hostované ve službě IIS 7.0 a novější má konzistenci napříč všechny koncové body, které zveřejňuje, i v případě, Některé z těchto koncových bodů použít jiné protokoly než HTTP).  
  
-   V doméně AppDomain funkce, které jsou implementovány modulem HTTP runtime použít obsah ASP.NET, ale ne WCF. Mnoho funkcí specifické platformy aplikace ASP.NET se nevztahují na služby WCF hostované v doméně AppDomain, která obsahuje obsahu ASP.NET. Mezi tyto funkce patří:  
  
    -   HttpContext: <xref:System.Web.HttpContext.Current%2A> je vždy `null` při přístupu z v rámci služby WCF. Použití <!--zz <xref:System.ServiceModel.OperationContext.Current.RequestContext>--> `RequestContext` místo.  
  
    -   Autorizace na základě souboru: Model zabezpečení WCF neumožňuje použití do souboru .svc služby při rozhodování o tom, jestli žádost o služby je autorizovaný seznam řízení přístupu (ACL).  
  
    -   Autorizace adres URL podle konfigurace: Obdobně model zabezpečení WCF nedrží se žádná pravidla ověřování na základě adresy URL zadaná v jeho System.Web \<autorizace > konfiguračního prvku. Tato nastavení jsou ignorovány požadavkům WCF, pokud se služba nachází v prostoru adresy URL zabezpečuje ASP. Autorizačních pravidel adres URL vaší sítě.  
  
    -   Rozšiřitelnost HttpModule: Infrastruktury hostování WCF zachycuje WCF při požadavků <xref:System.Web.HttpApplication.PostAuthenticateRequest> nevrací zpracování do kanálu HTTP technologie ASP.NET a je vyvolána událost. Moduly, které jsou naprogramovány tak, aby zachytávat žádosti v pozdějších fázích kanálu není zachytávat žádosti WCF.  
  
    -   Zosobnění technologie ASP.NET: Ve výchozím nastavení, WCF požaduje vždy spustí jako identita, procesu služby IIS i v případě, že technologie ASP.NET je nastavit pro povolení zosobnění pomocí vaší System.Web \<identity impersonate = "true" / > Možnosti konfigurace.  
  
 Tato omezení platí pouze pro služby WCF hostované v IIS aplikace. Chování obsahu ASP.NET nemá vliv na přítomnost WCF.  
  
 Aplikace WCF, které vyžadují funkce tradičně poskytované službou kanálu HTTP byste zvážit použití ekvivalenty WCF, které jsou hostiteli a přenosu nezávislé:  
  
-   <xref:System.ServiceModel.OperationContext> místo <xref:System.Web.HttpContext>.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> místo ASP. Autorizační soubor nebo adresa URL vaší sítě.  
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> nebo vlastní kanály namísto z modulů HTTP na základě úrovní.  
  
-   Zosobnění pro každou operaci pomocí technologie WCF místo System.Web zosobnění.  
  
 Alternativně můžete zvážit, službami v režimu kompatibility ASP.NET na WCF.  
  
## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>Hostování služby WCF v režim kompatibility ASP.NET  
 I když modelu WCF je určená chovat konzistentně napříč hostitelských prostředích a přenosy, jsou často scénáře, kde aplikace nevyžaduje, aby tento stupeň flexibilitu. Režim kompatibility ASP.NET na WCF je vhodné pro scénáře, které nevyžadují, aby možnost hostitele mimo službu IIS, nebo pro komunikaci pomocí jiné protokoly než HTTP, ale všechny funkce technologie ASP.NET webové aplikace platformy, které používají.  
  
 Na rozdíl od výchozí konfiguraci vedle sebe, kde infrastruktury hostování WCF zachycuje zpráv WCF a směruje je mimo kanálu protokolu HTTP, služby WCF spuštění v režimu kompatibility ASP.NET plně účastnit životního cyklu požadavku ASP.NET HTTP. V režimu kompatibility služby WCF pomocí kanálu HTTP prostřednictvím <xref:System.Web.IHttpHandler> implementace, podobně jako na způsob, jak požadavky pro stránky ASPX a ASMX webovými službami jsou zpracovány. V důsledku toho WCF se chová stejně jako ASMX s ohledem na tyto funkce technologie ASP.NET:  
  
-   <xref:System.Web.HttpContext>: WCF služby spuštěné v režimu kompatibility ASP.NET dostanete <xref:System.Web.HttpContext.Current%2A> a jeho přidruženého stavu.  
  
-   Autorizace na základě souboru: WCF služby spuštěné v režimu kompatibility ASP.NET může být zabezpečené pomocí souboru systému seznamy řízení přístupu (ACL) se připojuje k souboru .svc služby.  
  
-   Konfigurovatelné autorizace adres URL: ASP. NET. adresa URL autorizační pravidla se vynucují s ohledem požadavky WCF při spuštění služby WCF v režim kompatibility ASP.NET.  
  
-   <xref:System.Web.HttpModuleCollection> rozšíření: Protože WCF služby spuštěné v režimu kompatibility ASP.NET plně účastnit životního cyklu požadavku ASP.NET HTTP, jakýkoli modul HTTP nakonfigurované v kanálu HTTP je moct pracovat s WCF požadavky před i po vyvolání služby.  
  
-   Zosobnění technologie ASP.NET: Spuštění pomocí technologie ASP.NET aktuální identitu služby WCF zosobnit podproces, který může být jiný než identitu procesu služby IIS, pokud je povoleno zosobnění technologie ASP.NET pro aplikaci. Pokud zosobnění technologie ASP.NET a WCF zosobnění jsou povoleny pro konkrétní službu operace, implementace služby takže v konečném důsledku se spustí pomocí identity získané z WCF.  
  
 Režim kompatibility ASP.NET na WCF je povolené na úrovni aplikace provede následující konfigurací (umístěný v souboru Web.config aplikace):  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />  
</system.serviceModel>  
```  
  
 Výchozí hodnota je "`true`" Pokud nejsou zadané. Tuto hodnotu nastavíte na "`false`" označuje, že všechny služby WCF v aplikaci spuštěná nebude spuštěn v režimu kompatibility ASP.NET.  
  
 Protože režim kompatibility ASP.NET znamená sémantikou zpracování požadavku, které jsou zásadně liší od výchozího WCF, implementací jednotlivé služby mají možnost řízení, zda jsou provozovány v rámci aplikace, pro které technologie ASP.NET Režim kompatibility se povolila. Služby můžete použít <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> označující, jestli podporují režim kompatibility ASP.NET. Výchozí hodnota tohoto atributu je <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.  
  
 `[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]`  
  
 `public class CalculatorService : ICalculatorSession`  
  
 `{//Implement calculator service methods.}`  
  
 Následující tabulka ukazuje, jak nastavení režimu kompatibility celé aplikace komunikuje s jednotlivé služby uvedené úrovně podpory:  
  
|Nastavení režimu kompatibility celou aplikaci|[AspNetCompatibilityRequirementsMode]<br /><br /> Nastavení|Pozorovaných výsledků|  
|--------------------------------------------------|---------------------------------------------------------|---------------------|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Služba úspěšně aktivuje.|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Služba úspěšně aktivuje.|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Když služba přijímá zprávy, dojde k chybě aktivace.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Když služba přijímá zprávy, dojde k chybě aktivace.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Služba úspěšně aktivuje.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Služba úspěšně aktivuje.|  
  
> [!NOTE]
>  Služba IIS 7.0 a WAS umožňuje služeb WCF pro komunikaci pomocí jiné protokoly než HTTP. WCF služby spuštěné v aplikacích, které mají povolený režim kompatibility ASP.NET, ale nemáte oprávnění zpřístupňují koncové body jiným protokolem než HTTP. Taková konfigurace generuje výjimku aktivace, když služba přijímá jeho první zprávu.  
  
 Další informace o povolení režim kompatibility ASP.NET pro služby WCF najdete v tématu <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> a [režim kompatibility ASP.NET](../../../../docs/framework/wcf/samples/aspnet-compatibility.md) vzorku.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
