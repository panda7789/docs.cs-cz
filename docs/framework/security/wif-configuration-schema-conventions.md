---
title: "WIF konfigurace schématu konvence"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e327b45ddd260d1a52066b5bf53e7114100ff45c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wif-configuration-schema-conventions"></a><span data-ttu-id="08652-102">WIF konfigurace schématu konvence</span><span class="sxs-lookup"><span data-stu-id="08652-102">WIF Configuration Schema Conventions</span></span>
<span data-ttu-id="08652-103">Toto téma popisuje konvence používaných v celém témata týkající se konfigurace Windows Identity Foundation (WIF) a popisuje některé běžné funkce a atributy se používají v [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) a [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) oddíly.</span><span class="sxs-lookup"><span data-stu-id="08652-103">This topic discusses conventions used throughout the Windows Identity Foundation (WIF) configuration topics and describes some common features and attributes used in the [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) and the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) sections.</span></span>  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a><span data-ttu-id="08652-104">Režimy</span><span class="sxs-lookup"><span data-stu-id="08652-104">Modes</span></span>  
 <span data-ttu-id="08652-105">Mnoho konfigurační prvky WIF má `mode` atribut.</span><span class="sxs-lookup"><span data-stu-id="08652-105">Many of the WIF configuration elements have a `mode` attribute.</span></span> <span data-ttu-id="08652-106">Obvykle se tento atribut určuje, které třída se používá k provést určitou část zpracování a které konfigurační prvky jsou povoleny jako podřízené prvky aktuálního elementu.</span><span class="sxs-lookup"><span data-stu-id="08652-106">This attribute typically controls which class is used to do a particular part of the processing and which configuration elements are allowed as child elements of the current element.</span></span> <span data-ttu-id="08652-107">Pokud elementy, které jsou zahrnuty v konfiguračním souboru se ignorují kvůli nastavení režimu, bude vyvolána chyba konfigurace.</span><span class="sxs-lookup"><span data-stu-id="08652-107">A configuration error will be raised if elements that are included in the configuration file are ignored because of the mode settings.</span></span>  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a><span data-ttu-id="08652-108">Časový interval hodnoty</span><span class="sxs-lookup"><span data-stu-id="08652-108">Timespan Values</span></span>  
 <span data-ttu-id="08652-109">Kde <xref:System.TimeSpan> je použít jako typ atributu, najdete v článku <xref:System.TimeSpan.Parse%28System.String%29> metoda zobrazíte povolené formátu.</span><span class="sxs-lookup"><span data-stu-id="08652-109">Where <xref:System.TimeSpan> is used as the type of an attribute, see the <xref:System.TimeSpan.Parse%28System.String%29> method to see the allowed format.</span></span> <span data-ttu-id="08652-110">Tento formát odpovídá specifikaci následující.</span><span class="sxs-lookup"><span data-stu-id="08652-110">This format conforms to the following specification.</span></span>  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 <span data-ttu-id="08652-111">Například "30", "30.00:00", "30.00:00:00" všechny znamená 30 dní; a "00:05", "00: 05:00", "0.00:05:00.00" všechny znamenat 5 minut.</span><span class="sxs-lookup"><span data-stu-id="08652-111">For example, "30", "30.00:00", "30.00:00:00" all mean 30 days; and "00:05", "00:05:00", "0.00:05:00.00" all mean 5 minutes.</span></span>  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a><span data-ttu-id="08652-112">Odkazy na certifikát</span><span class="sxs-lookup"><span data-stu-id="08652-112">Certificate References</span></span>  
 <span data-ttu-id="08652-113">Odkazy na certifikáty pomocí trvat několik elementů `<certificateReference>` elementu.</span><span class="sxs-lookup"><span data-stu-id="08652-113">Several elements take references to certificates using the `<certificateReference>` element.</span></span> <span data-ttu-id="08652-114">Při odkazování na certifikát, jsou k dispozici následující atributy.</span><span class="sxs-lookup"><span data-stu-id="08652-114">When referencing a certificate, the following attributes are available.</span></span>  
  
|||  
|-|-|  
|`storeLocation`|<span data-ttu-id="08652-115">Hodnota <xref:System.Security.Cryptography.X509Certificates.StoreLocation> výčtu: `CurrentUser` nebo `CurrentMachine`.</span><span class="sxs-lookup"><span data-stu-id="08652-115">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreLocation> enumeration: `CurrentUser` or `CurrentMachine`.</span></span>|  
|`storeName`|<span data-ttu-id="08652-116">Hodnota <xref:System.Security.Cryptography.X509Certificates.StoreName> výčtu; velmi užitečné pro tento kontext se `My` a `TrustedPeople`.</span><span class="sxs-lookup"><span data-stu-id="08652-116">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreName> enumeration; the most useful for this context are `My` and `TrustedPeople`.</span></span>|  
|`x509FindType`|<span data-ttu-id="08652-117">Hodnota <xref:System.Security.Cryptography.X509Certificates.X509FindType> výčtu; velmi užitečné pro tento kontext se `FindBySubjectName` a `FindByThumbprint`.</span><span class="sxs-lookup"><span data-stu-id="08652-117">A value of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> enumeration; the most useful for this context are `FindBySubjectName` and `FindByThumbprint`.</span></span> <span data-ttu-id="08652-118">Omezit riziko chyby, doporučujeme `FindByThumbprint` typ, který používat v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="08652-118">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span>|  
|`findValue`|<span data-ttu-id="08652-119">Hodnota použít k vyhledání certifikátu, založená na `x509FindType` atribut.</span><span class="sxs-lookup"><span data-stu-id="08652-119">The value used to find the certificate, based on the `x509FindType` attribute.</span></span> <span data-ttu-id="08652-120">Omezit riziko chyby, doporučujeme `FindByThumbprint` typ, který používat v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="08652-120">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span> <span data-ttu-id="08652-121">Když `FindByThumbPrint` je zadán, přebírá hodnotu, která je hexadecimální řetězec formátu certifikát tento atribut kryptografický otisk, například "97249e1a5fa6bee5e515b82111ef524a4c91583f".</span><span class="sxs-lookup"><span data-stu-id="08652-121">When `FindByThumbPrint` is specified, this attribute takes a value that is the hexadecimal-string form of the certificate thumbprint; for example, "97249e1a5fa6bee5e515b82111ef524a4c91583f".</span></span>|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a><span data-ttu-id="08652-122">Odkazy na vlastní typ</span><span class="sxs-lookup"><span data-stu-id="08652-122">Custom Type References</span></span>  
 <span data-ttu-id="08652-123">Referenční dokumentace několik elementů vlastních typů pomocí `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="08652-123">Several elements reference custom types using the `type` attribute.</span></span> <span data-ttu-id="08652-124">Tento atribut musí určovat název vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="08652-124">This attribute should specify the name of the custom type.</span></span> <span data-ttu-id="08652-125">Chcete-li typ z globální mezipaměti sestavení (GAC), je třeba použít silným názvem.</span><span class="sxs-lookup"><span data-stu-id="08652-125">To reference a type from the Global Assembly Cache (GAC), a strong name should be used.</span></span> <span data-ttu-id="08652-126">Chcete-li typu ze sestavení v přihrádce / adresáře, může použít jednoduchý odkaz na sestavení kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="08652-126">To reference a type from an assembly in the Bin/ directory, a simple assembly-qualified reference may be used.</span></span> <span data-ttu-id="08652-127">Typy definované v adresáři App_Code nebo adresáře může také odkazovat ze stačí zadat název typu s žádné opravňující sestavení.</span><span class="sxs-lookup"><span data-stu-id="08652-127">Types defined in the App_Code/ directory may also be referenced by simply specifying the type name with no qualifying assembly.</span></span>  
  
 <span data-ttu-id="08652-128">Vlastní typy musí být odvozen od typu určeného a musí zadat `public` výchozí konstruktor (0 argumentů).</span><span class="sxs-lookup"><span data-stu-id="08652-128">Custom types must be derived from the type specified and they must provide a `public` default (0 argument) constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08652-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="08652-129">See Also</span></span>  
 [<span data-ttu-id="08652-130">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="08652-130">\<system.identityModel></span></span>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)  
 [<span data-ttu-id="08652-131">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="08652-131">\<system.identityModel.services></span></span>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
