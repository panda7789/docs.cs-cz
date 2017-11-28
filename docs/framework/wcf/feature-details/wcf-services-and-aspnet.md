---
title: "Služby WCF a ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c86ab6996b85e679fc5c15d85e86d25eaa8b1844
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-services-and-aspnet"></a>Služby WCF a ASP.NET
Toto téma popisuje hostování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služeb souběžného s ASP.NET a jejich hostování v režimu kompatibility ASP.NET.  
  
## <a name="hosting-wcf-side-by-side-with-aspnet"></a>Hostování WCF-souběžného s technologií ASP.NET  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]s můžou být služby hostované v Internetové informační služby (IIS). Stránky ASPX a ASMX webové služby v rámci jedné, běžné domény aplikace. Technologie ASP.NET poskytuje obecné služby infrastruktury, jako je Správa AppDomain a dynamická kompilace pro obě [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a prostředí runtime ASP.NET HTTP. Výchozí konfiguraci pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je vedle sebe s technologií ASP.NET.  
  
 ![Služby WCF a rozhraní ASP .NET: sdílení stavu](../../../../docs/framework/wcf/feature-details/media/hostingwcfwithaspnet.gif "HostingWCFwithASPNET")  
  
 Modul runtime ASP.NET HTTP zpracovává požadavky na technologii ASP.NET, ale není součástí zpracování požadavků určených pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, i když tyto služby jsou hostované do stejné domény aplikace, jako je ASP.NET obsahu. Místo toho [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Model služby zachytí zprávy adresované do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby a směruje je prostřednictvím [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přenosu/kanál zásobníku.  
  
 Výsledky vedle sebe modelu jsou následující:  
  
-   ASP.NET a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services můžete sdílet AppDomain stavu. Vzhledem k tomu, že dvě rozhraní mohou existovat vedle sebe do stejné domény aplikace, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AppDomain stavu můžete také sdílet s technologií ASP.NET (včetně statické proměnné, události a tak dále).  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby chovat konzistentně, nezávisle na hostování prostředí a přenosu. Modul runtime ASP.NET HTTP je záměrně vázány na IIS/ASP.NET hostování prostředí a komunikaci pomocí protokolu HTTP. Naopak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] slouží k chovat konzistentně napříč hostitelská prostředí ([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] chová konzistentně obě uvnitř i vně IIS) a přes přenosu (služby hostované ve službě IIS 7.0 nebo novější je konzistentní chování napříč všemi Koncové body zpřístupňuje, i když některé z těchto koncových bodů použít jiné protokoly než HTTP).  
  
-   V objektu AppDomain použít funkce implementované HTTP runtime ASP.NET obsah, ale nikoli k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Mnoho funkcí specifické platformy aplikace ASP.NET se nevztahují na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby hostované v objektu AppDomain, který obsahuje obsahu ASP.NET. Mezi tyto funkce patří:  
  
    -   Položka HttpContext: <xref:System.Web.HttpContext.Current%2A> je vždy `null` přistupováno z uvnitř [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. Použití <!--zz <xref:System.ServiceModel.OperationContext.Current.RequestContext>--> `RequestContext` místo.  
  
    -   Na základě souborů autorizace: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model zabezpečení nepovoluje seznamu řízení přístupu (ACL) u souboru .svc služby při rozhodování, jestli je autorizovaný žádost o služby.  
  
    -   Autorizace adres URL na základě konfigurace: Podobně [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model zabezpečení není ve správném všechna pravidla autorizace na základě adresy URL zadané v System.Web na \<autorizace > konfigurační prvek. Tato nastavení ignorují pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] požadavky, pokud se služba nachází v prostoru adresy URL zabezpečeny ASP. NET na autorizačních pravidel adres URL.  
  
    -   Rozšíření modulu http: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hostování infrastruktury zachycuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] požadavky, když <xref:System.Web.HttpApplication.PostAuthenticateRequest> nevrací zpracování kanálu ASP.NET protokolu HTTP a je vyvolána událost. Moduly, které jsou programového za účelem zachycení požadavků na novější fázemi kanálu není intercept [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] požadavky.  
  
    -   Zosobnění technologie ASP.NET: ve výchozím nastavení, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] požadavků vždy běží jako služba IIS zpracovávat identitu, i v případě, že technologie ASP.NET je nastavit pro povolení zosobnění pomocí na System.Web \<zosobnit identitu = "true" / > Možnosti konfigurace.  
  
 Tato omezení platí pouze pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby hostované v aplikaci služby IIS. Chování obsahu ASP.NET nemá vliv na přítomnost [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]aplikace, které vyžadují funkce tradičně poskytované službou kanál protokolu HTTP byste měli zvážit použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ekvivalenty, které jsou hostiteli a přenosu nezávislé:  
  
-   <xref:System.ServiceModel.OperationContext>místo <xref:System.Web.HttpContext>.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>místo ASP. NET na soubor nebo adresa URL autorizace.  
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector>nebo vlastní vrstveného kanály místo vytváření modulů HTTP.  
  
-   Zosobnění pro každou operaci pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] místo System.Web zosobnění.  
  
 Alternativně můžete zvážit službami [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]na režim kompatibility ASP.NET.  
  
## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>Hostování služby WCF v režimu kompatibility ASP.NET  
 I když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model je určen k chovat konzistentně napříč hostitelských prostředích a přenosy, jsou často scénáře, kde aplikace nevyžaduje takové pružnosti. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]na režim kompatibility ASP.NET je vhodná pro scénáře, který nevyžaduje možnost k hostování mimo služby IIS nebo pro komunikaci pomocí jiné protokoly než HTTP, ale který použít všechny funkce na platformě ASP.NET – webové aplikace.  
  
 Na rozdíl od výchozí souběžně sdílená konfigurace, kde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hostování infrastruktury zachycuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zprávy a směruje je mimo kanál protokolu HTTP, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby spuštěné v režimu kompatibility ASP.NET účast ve plně životní cyklus požadavku HTTP technologie ASP.NET. V režimu kompatibility [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby používat přes kanál protokolu HTTP <xref:System.Web.IHttpHandler> implementace, podobně jako na požadavky na způsob pro stránky ASPX a ASMX webových služeb jsou zpracovávány. V důsledku toho [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se chová stejně ASMX s ohledem na tyto funkce ASP.NET:  
  
-   <xref:System.Web.HttpContext>: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby spuštěné v režimu kompatibility ASP.NET můžete k <xref:System.Web.HttpContext.Current%2A> a jeho přidružený stav.  
  
-   Na základě souborů autorizace: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby spuštěné v režimu kompatibility ASP.NET může být zabezpečené pomocí souborového systému seznamy řízení přístupu (ACL) se připojuje k souboru .svc služby.  
  
-   Konfigurovat autorizace adres URL: ASP. Autorizačních pravidel adres URL na NET prosazují pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] požadavky, když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba běží v režimu kompatibility ASP.NET.  
  
-   <xref:System.Web.HttpModuleCollection>rozšiřitelnost: protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby spuštěné v režimu kompatibility ASP.NET plně účastnit v životním cyklu požadavku HTTP technologie ASP.NET, je možné pracovat libovolný modul HTTP nakonfigurované v kanálu HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] požadavky před i po volání služby.  
  
-   Zosobnění technologie ASP.NET: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby spouštět s využitím aktuální identitu ASP.NET zosobnit podproces, který může být jiný než identitě procesu služby IIS, pokud bylo povoleno zosobnění technologie ASP.NET pro aplikaci. Pokud zosobnění technologie ASP.NET a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zosobnění jsou povoleny pro konkrétní službu operaci, nakonec běží implementace služby pomocí identity získané z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]na režim kompatibility ASP.NET je povolena na úrovni aplikace pomocí následující konfigurace (nachází se v souboru Web.config aplikace):  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />  
</system.serviceModel>  
```  
  
 Výchozí hodnota je "`true`" Pokud není zadaný. Nastavení této hodnoty na "`false`" znamená, že všechny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby spuštěné v aplikaci nebude možné spustit v režimu kompatibility ASP.NET.  
  
 Protože režim kompatibility ASP.NET znamená sémantiku zpracování požadavku, která se zásadně liší od [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] výchozí implementace jednotlivých služeb mít možnost řídit, jestli se spustit v rámci aplikace pro které ASP. Režim kompatibility NET byla povolena. Služby, můžou používat <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> indikující, zda podporují režim kompatibility ASP.NET. Výchozí hodnota pro tento atribut je <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.  
  
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
>  Umožňuje službě IIS 7.0 a WAS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby pro komunikaci pomocí jiné protokoly než HTTP. Ale [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vystavit jiným protokolem než HTTP koncových bodů nejsou povoleny služby spuštěné v aplikacích, které jste povolili režim kompatibility ASP.NET. Taková konfigurace generuje výjimku aktivace, když služba přijme jeho první zprávy.  
  
 Další informace o povolení režim kompatibility ASP.NET pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, najdete v části <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> a [režim kompatibility ASP.NET](../../../../docs/framework/wcf/samples/aspnet-compatibility.md) ukázka.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
