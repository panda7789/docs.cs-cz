---
title: Služby WCF a ASP.NET
description: Přečtěte si o hostování služeb WCF vedle sebe pomocí ASP.NET a jejich hostování v režimu kompatibility ASP.NET.
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 1d7401f6a326bc50923123acf803e26ce8238415
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246412"
---
# <a name="wcf-services-and-aspnet"></a>Služby WCF a ASP.NET

Toto téma popisuje služby hostování Windows Communication Foundation (WCF) vedle sebe pomocí ASP.NET a jejich hostování v režimu kompatibility ASP.NET.

## <a name="hosting-wcf-side-by-side-with-aspnet"></a>Hostování WCF vedle sebe pomocí ASP.NET

Služby WCF hostované ve službě Internetová informační služba (IIS) se můžou nacházet pomocí. Stránky ASPX a webové služby ASMX v rámci jedné běžné aplikační domény. ASP.NET poskytuje běžné služby infrastruktury, jako je například Správa AppDomain a dynamická kompilace pro WCF i modul HTTP runtime ASP.NET. Výchozí konfigurace pro WCF je souběžná s ASP.NET.

![Snímek obrazovky zobrazující služby WCF a ASP .NET: stav sdílení](./media/wcf-services-and-aspnet/windows-communication-foundation-services-asp-dotnet-configuration.gif)

Modul runtime ASP.NET HTTP zpracovává požadavky ASP.NET, ale nepodílí se na zpracování požadavků určených pro služby WCF, i když jsou tyto služby hostovány ve stejné doméně AppDomain jako obsah ASP.NET. Místo toho model služby WCF zachycuje zprávy adresované službám WCF a směruje je prostřednictvím zásobníku přenosu nebo kanálu WCF.

Výsledky souběžného modelu jsou následující:

- Služby ASP.NET a WCF můžou sdílet stav domény AppDomain. Vzhledem k tomu, že dvě architektury mohou existovat ve stejné doméně AppDomain, může WCF také sdílet stav domény AppDomain s ASP.NET (včetně statických proměnných, událostí atd.).

- Služby WCF se chovají konzistentně, nezávisle na hostitelském prostředí a přenosu. Běhový modul HTTP ASP.NET je záměrně spojený s hostitelským prostředím služby IIS/ASP. NET a komunikace HTTP. Služba WCF je naopak navržena tak, aby se chovala konzistentně napříč hostitelskými prostředími (WCF se chová konzistentně uvnitř i vně služby IIS) a napříč přenosem (služba hostovaná ve službě IIS 7,0 a novější má konzistentní chování ve všech koncových bodech, které zpřístupňuje), i když některé z těchto koncových bodů používají jiné protokoly než HTTP).

- V rámci třídy AppDomain se funkce implementované modulem HTTP runtime vztahují na obsah ASP.NET, ale ne na WCF. Mnoho funkcí specifických pro protokol HTTP platformy aplikace ASP.NET se nevztahuje na služby WCF hostované v doméně AppDomain, která obsahuje obsah ASP.NET. Mezi tyto funkce patří následující:

  - HttpContext: <xref:System.Web.HttpContext.Current%2A> je vždy `null` k dispozici v rámci služby WCF. Místo toho použijte <xref:System.ServiceModel.Channels.RequestContext>.

  - Ověřování na základě souborů: model zabezpečení WCF nepovoluje přístup k seznamu řízení přístupu (ACL), který se používá pro soubor. svc služby při rozhodování, zda je žádost o službu autorizována.

  - Autorizace adresy URL založené na konfiguraci: podobně, model zabezpečení WCF nedodržuje žádná autorizační pravidla založená na adrese URL zadaná v konfiguračním elementu System. Web \<authorization> . Tato nastavení se u požadavků WCF ignorují, pokud se služba nachází v prostoru URL zabezpečeném pomocí ASP. NETTO autorizační pravidla URL.

  - Rozšiřitelnost HttpModule: infrastruktura hostování WCF zachycuje požadavky WCF při <xref:System.Web.HttpApplication.PostAuthenticateRequest> vyvolání události a nevrátí zpracování do kanálu HTTP ASP.NET. Moduly, které jsou kódované pro zachycení požadavků v pozdějších fázích kanálu, nezachycují požadavky WCF.

  - Zosobnění ASP.NET: ve výchozím nastavení se požadavky WCF vždy spouštějí jako identita procesu IIS, a to i v případě, že ASP.NET je nastavená tak, aby povolovala zosobnění pomocí možnosti konfigurace System. Web. \<identity impersonate="true" />

Tato omezení platí jenom pro služby WCF hostované v aplikaci IIS. Chování ASP.NET obsahu není ovlivněno přítomností služby WCF.

Aplikace WCF, které vyžadují funkčnost, tradičně poskytované kanálem HTTP, by měly uvažovat o použití ekvivalentů WCF, což jsou nezávislé na hostiteli a přenosu:

- <xref:System.ServiceModel.OperationContext>místo <xref:System.Web.HttpContext> .

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>místo ASP. Ověřování souboru nebo adresy URL netto.

- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector>nebo vlastní vrstvené kanály namísto modulů HTTP.

- Zosobnění pro každou operaci pomocí WCF namísto zosobnění System. Web.

Případně můžete zvážit spuštění služeb v režimu kompatibility ASP.NET WCF.

## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>Hostování služeb WCF v režimu kompatibility ASP.NET

I když je model WCF navržený tak, aby se choval konzistentně napříč hostitelskými prostředími a přenosy, často se jedná o scénáře, kdy aplikace nevyžaduje tuto míru flexibility. Režim kompatibility ASP.NET WCF je vhodný pro scénáře, které nevyžadují schopnost hostovat mimo službu IIS nebo komunikovat přes jiné protokoly než HTTP, ale používá všechny funkce platformy webové aplikace ASP.NET.

Na rozdíl od výchozí souběžné konfigurace, kde infrastruktura hostování WCF zachycuje zprávy WCF a směruje je z kanálu HTTP, se služby WCF běžící v režimu kompatibility ASP.NET plně podílejí v životním cyklu žádosti ASP.NET HTTP. V režimu kompatibility používají služby WCF kanál HTTP prostřednictvím <xref:System.Web.IHttpHandler> implementace, podobně jako zpracování požadavků na stránky ASPX a webové služby ASMX. V důsledku toho se WCF chová stejně jako ASMX s ohledem na následující funkce ASP.NET:

- <xref:System.Web.HttpContext>: Služby WCF spuštěné v režimu kompatibility ASP.NET mají přístup k <xref:System.Web.HttpContext.Current%2A> jeho přidruženému stavu.

- Autorizace na základě souborů: služby WCF běžící v režimu kompatibility ASP.NET můžou být zabezpečené připojením seznamů řízení přístupu (ACL) systému souborů do souboru. svc služby.

- Konfigurovatelná autorizace adresy URL: ASP. Autorizační pravidla adresy URL netto se vynutily pro požadavky WCF, když je služba WCF spuštěná v režimu kompatibility ASP.NET.

- <xref:System.Web.HttpModuleCollection>Rozšiřitelnost: vzhledem k tomu, že se služby WCF běžící v režimu kompatibility ASP.NET plně účastní životního cyklu žádosti ASP.NET HTTP, jakýkoli modul HTTP konfigurovaný v kanálu HTTP je schopný pracovat na žádostech WCF před i po vyvolání služby.

- Zosobnění ASP.NET: služby WCF běží pomocí aktuální identity ASP.NET zosobněného vlákna, které se může lišit od identity procesu služby IIS, pokud je pro aplikaci povolené zosobnění ASP.NET. Pokud jsou pro určitou operaci služby povolené zosobnění ASP.NET a zosobnění WCF, implementace služby se nakonec spustí pomocí identity získané od služby WCF.

Režim kompatibility ASP.NET WCF je povolený na úrovni aplikace pomocí následující konfigurace (umístěná v souboru Web.config aplikace):

```xml
<system.serviceModel>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```

Tato hodnota se nastaví na výchozí hodnotu, `false` Pokud není zadána. Hodnota `false` označuje, že všechny služby WCF spuštěné v aplikaci nebudou spuštěny v režimu kompatibility ASP.NET.

Vzhledem k tomu, že režim kompatibility ASP.NET zahrnuje sémantiku zpracování požadavků, která se zásadním rozdílem od výchozího nastavení WCF liší, jednotlivé implementace služeb mají možnost řídit, jestli se spouštějí v aplikaci, pro kterou je povolený režim kompatibility ASP.NET. Služby mohou používat <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> k označení, zda podporují režim kompatibility ASP.NET. Výchozí hodnota pro tento atribut je <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.

```csharp
[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
public class CalculatorService : ICalculatorSession
{//Implement calculator service methods.}
```

Následující tabulka ukazuje, jak nastavení režimu kompatibility v rámci aplikace komunikuje s úrovní podpory, která je uvedena v jednotlivých službách:

|Nastavení režimu kompatibility na úrovni aplikace|AspNetCompatibilityRequirementsMode<br /><br /> Nastavení|Zjištěný výsledek|
|--------------------------------------------------|---------------------------------------------------------|---------------------|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Služba se úspěšně aktivovala.|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Služba se úspěšně aktivovala.|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Pokud služba obdrží zprávu, dojde k chybě aktivace.|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Pokud služba obdrží zprávu, dojde k chybě aktivace.|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Služba se úspěšně aktivovala.|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Služba se úspěšně aktivovala.|

> [!NOTE]
> Služba IIS 7,0 a byla umožněna službě WCF komunikovat přes jiné protokoly než HTTP. Služby WCF spuštěné v aplikacích, které mají povolený režim kompatibility ASP.NET, však nejsou povoleny pro zobrazení koncových bodů jiných než HTTP. Taková konfigurace vygeneruje výjimku aktivace, když služba obdrží svou první zprávu.

Další informace o povolení režimu kompatibility ASP.NET pro služby WCF najdete v tématu <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> a v ukázce [kompatibility ASP.NET](../samples/aspnet-compatibility.md) .

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
