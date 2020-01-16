---
title: Konfigurace Internetové informační služby 7.0 pro službu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 41eedcf78d8ca6f10fcd0380e43420dcc1b328f1
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964509"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="63fa9-102">Konfigurace Internetové informační služby 7.0 pro službu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="63fa9-102">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>

<span data-ttu-id="63fa9-103">Internetová informační služba (IIS) 7,0 má modulární návrh, který umožňuje selektivní instalaci požadovaných součástí.</span><span class="sxs-lookup"><span data-stu-id="63fa9-103">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="63fa9-104">Tento návrh je založený na nové technologii komponenty založené na manifestech, kterou přináší Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="63fa9-104">This design is based on the new manifest-driven componentization technology introduced in Windows Vista.</span></span> <span data-ttu-id="63fa9-105">Existuje více než 40 samostatných součástí služby IIS 7,0, které je možné nainstalovat nezávisle.</span><span class="sxs-lookup"><span data-stu-id="63fa9-105">There are more than 40 standalone feature components of IIS 7.0 that can be installed independently.</span></span> <span data-ttu-id="63fa9-106">IT profesionálům umožňuje snadno přizpůsobit instalaci podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="63fa9-106">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="63fa9-107">Toto téma popisuje, jak nakonfigurovat službu IIS 7,0 pro použití s Windows Communication Foundation (WCF) a určit, které součásti jsou nutné.</span><span class="sxs-lookup"><span data-stu-id="63fa9-107">This topic discusses how to configure IIS 7.0 for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>

## <a name="minimal-installation-installing-was"></a><span data-ttu-id="63fa9-108">Minimální instalace: Instalace byla</span><span class="sxs-lookup"><span data-stu-id="63fa9-108">Minimal Installation: Installing WAS</span></span>
 <span data-ttu-id="63fa9-109">Minimální instalací celého balíčku služby IIS 7,0 je instalace aktivační služby procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="63fa9-109">The minimal installation of the whole IIS 7.0 package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="63fa9-110">WAS je samostatná funkce, která je jedinou funkcí ze služby IIS 7,0, která je dostupná pro všechny operační systémy Windows Vista (Home Basic, Home Premium, Business a Ultimate a Enterprise).</span><span class="sxs-lookup"><span data-stu-id="63fa9-110">WAS is a standalone feature and it is the only feature from the IIS 7.0 that is available for all Windows Vista operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>

 <span data-ttu-id="63fa9-111">V Ovládacích panelech klikněte na **programy** a potom klikněte na **zapnout nebo vypnout funkce systému Windows** , které jsou uvedené v části **programy a funkce**. v seznamu se zobrazí tato součást jako na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="63fa9-111">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>

 <span data-ttu-id="63fa9-112">![Zapnout nebo vypnout funkce dialogového okna](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="63fa9-112">![Turn Features On or Off Dialog](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>

 <span data-ttu-id="63fa9-113">Tato funkce má následující dílčí komponenty:</span><span class="sxs-lookup"><span data-stu-id="63fa9-113">This feature has the following sub-components:</span></span>

- <span data-ttu-id="63fa9-114">Prostředí .NET</span><span class="sxs-lookup"><span data-stu-id="63fa9-114">.NET Environment</span></span>

- <span data-ttu-id="63fa9-115">Rozhraní API pro konfiguraci</span><span class="sxs-lookup"><span data-stu-id="63fa9-115">Configuration APIs</span></span>

- <span data-ttu-id="63fa9-116">Model procesu</span><span class="sxs-lookup"><span data-stu-id="63fa9-116">Process Model</span></span>

 <span data-ttu-id="63fa9-117">Pokud vyberete kořenový uzel, bude ve výchozím nastavení kontrolován pouze dílčí uzel **modelu procesu** .</span><span class="sxs-lookup"><span data-stu-id="63fa9-117">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="63fa9-118">Počítejte s tím, že při instalaci, kterou nainstalujete, byla nainstalována pouze aplikace, protože není k dispozici podpora webového serveru.</span><span class="sxs-lookup"><span data-stu-id="63fa9-118">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>

 <span data-ttu-id="63fa9-119">Pokud chcete zajistit, aby WCF nebo aplikace ASP.NET fungovaly, zaškrtněte políčko **prostředí .NET** .</span><span class="sxs-lookup"><span data-stu-id="63fa9-119">To make WCF or any ASP.NET application work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="63fa9-120">To znamená, že všechny komponenty byly potřebné k tomu, aby služba WCF a ASP.NET správně fungovala.</span><span class="sxs-lookup"><span data-stu-id="63fa9-120">This means that all of WAS components are required to make WCF and ASP.NET to work well.</span></span> <span data-ttu-id="63fa9-121">Tyto součásti jsou automaticky kontrolovány po instalaci kterékoli z těchto součástí.</span><span class="sxs-lookup"><span data-stu-id="63fa9-121">These are automatically checked once you install any of those components.</span></span>

## <a name="iis-70-default-installation"></a><span data-ttu-id="63fa9-122">IIS 7,0: výchozí instalace</span><span class="sxs-lookup"><span data-stu-id="63fa9-122">IIS 7.0: Default Installation</span></span>
 <span data-ttu-id="63fa9-123">Zaškrtnutím funkce **Internetová informační služba** se některé dílčí uzly automaticky zkontrolují, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="63fa9-123">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>

 <span data-ttu-id="63fa9-124">![Výchozí nastavení pro funkce IIS 7,0](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="63fa9-124">![Default settings for IIS 7.0 features](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>

 <span data-ttu-id="63fa9-125">Toto je výchozí instalace služby IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="63fa9-125">This is the default installation of IIS 7.0.</span></span> <span data-ttu-id="63fa9-126">V rámci této instalace můžete použít službu IIS 7,0 pro obsluhu statického obsahu (například stránky HTML a další obsah).</span><span class="sxs-lookup"><span data-stu-id="63fa9-126">With this installation, you can use IIS 7.0 to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="63fa9-127">Nemůžete ale spouštět aplikace ASP.NET nebo CGI ani hostitelské služby WCF.</span><span class="sxs-lookup"><span data-stu-id="63fa9-127">However, you cannot run ASP.NET or CGI applications or host WCF services.</span></span>

## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="63fa9-128">IIS 7,0: instalace s podporou ASP.NET</span><span class="sxs-lookup"><span data-stu-id="63fa9-128">IIS 7.0: Installation with ASP.NET Support</span></span>
 <span data-ttu-id="63fa9-129">Abyste mohli ASP.NET pracovat na IIS 7,0, musíte nainstalovat ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="63fa9-129">You must install ASP.NET to make ASP.NET work on IIS 7.0.</span></span> <span data-ttu-id="63fa9-130">Po kontrole **ASP.NET**by měla obrazovka vypadat jako na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="63fa9-130">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>

 <span data-ttu-id="63fa9-131">![Asp.NET – požadovaná nastavení](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="63fa9-131">![Asp.NET required settings](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>

 <span data-ttu-id="63fa9-132">Toto je minimální prostředí pro aplikace WCF a ASP.NET, aby fungovalo ve službě IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="63fa9-132">This is the minimal environment for both WCF and ASP.NET applications to work in IIS 7.0.</span></span>

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="63fa9-133">IIS 7,0: instalace se součástmi kompatibility IIS 6,0</span><span class="sxs-lookup"><span data-stu-id="63fa9-133">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>
 <span data-ttu-id="63fa9-134">Při instalaci IIS 7,0 na systém se sadou Visual Studio 2005 nebo některé jiné skripty nebo nástroje pro automatizaci (například Adsutil. vbs), které konfigurují virtuální aplikace, které používají službu IIS 6,0 API, se ujistěte, že jste zkontrolovali **Nástroje pro skriptování**služby iis na 6,0.</span><span class="sxs-lookup"><span data-stu-id="63fa9-134">When installing IIS 7.0 on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use IIS 6.0 Metabase API, ensure that you check the IIS 6.0 **Scripting Tools**.</span></span> <span data-ttu-id="63fa9-135">Tím se automaticky zkontroluje ostatní poduzly **kompatibility správy**služby IIS 6,0.</span><span class="sxs-lookup"><span data-stu-id="63fa9-135">This automatically checks the other sub-nodes of IIS 6.0 **Management Compatibility**.</span></span> <span data-ttu-id="63fa9-136">Následující ilustrace znázorňuje obrazovku po dokončení:</span><span class="sxs-lookup"><span data-stu-id="63fa9-136">The following illustration shows the screen after this is done:</span></span>

 <span data-ttu-id="63fa9-137">![Nastavení kompatibility správy služby IIS 6,0](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="63fa9-137">![IIS 6.0 Management Compatibility Settings](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>

 <span data-ttu-id="63fa9-138">V rámci této instalace máte vše potřebné k používání funkcí IIS 7,0, ASP.NET a WCF a ukázek, které jsou k dispozici na webu.</span><span class="sxs-lookup"><span data-stu-id="63fa9-138">With this installation, you have everything required to use IIS 7.0, ASP.NET and WCF features and samples available on the Web.</span></span>

## <a name="request-limits"></a><span data-ttu-id="63fa9-139">Omezení počtu požadavků</span><span class="sxs-lookup"><span data-stu-id="63fa9-139">Request Limits</span></span>
 <span data-ttu-id="63fa9-140">V systému Windows Vista se službou IIS 7 byla změněna výchozí hodnota `maxUri` a nastavení `maxQueryStringSize`.</span><span class="sxs-lookup"><span data-stu-id="63fa9-140">On Windows Vista with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="63fa9-141">Ve výchozím nastavení umožňuje filtrování požadavků ve službě IIS 7,0 délku adresy URL 4096 znaků a délka řetězce dotazu 2048 znaků.</span><span class="sxs-lookup"><span data-stu-id="63fa9-141">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="63fa9-142">Chcete-li změnit tyto výchozí hodnoty, přidejte do souboru App. config následující kód XML.</span><span class="sxs-lookup"><span data-stu-id="63fa9-142">To change these defaults add the following XML to your App.config file.</span></span>

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a><span data-ttu-id="63fa9-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63fa9-143">See also</span></span>

- [<span data-ttu-id="63fa9-144">Architektura aktivace WAS</span><span class="sxs-lookup"><span data-stu-id="63fa9-144">WAS Activation Architecture</span></span>](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [<span data-ttu-id="63fa9-145">Konfigurace WAS pro použití s WCF</span><span class="sxs-lookup"><span data-stu-id="63fa9-145">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [<span data-ttu-id="63fa9-146">Postupy: Instalace a konfigurace aktivačních komponent WCF</span><span class="sxs-lookup"><span data-stu-id="63fa9-146">How to: Install and Configure WCF Activation Components</span></span>](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- <span data-ttu-id="63fa9-147">[Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="63fa9-147">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
