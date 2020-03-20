---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152577"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="1c19b-101">\<> serviceTokenResolver</span><span class="sxs-lookup"><span data-stu-id="1c19b-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="1c19b-102">Registruje překladač tokenů služby, který používají obslužné rutiny v kolekci obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="1c19b-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="1c19b-103">Překládání tokenů služby se používá k překladu šifrovacího tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="1c19b-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="1c19b-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1c19b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1c19b-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="1c19b-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="1c19b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="1c19b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="1c19b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="1c19b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="1c19b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="1c19b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="1c19b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span><span class="sxs-lookup"><span data-stu-id="1c19b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c19b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c19b-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c19b-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1c19b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1c19b-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1c19b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c19b-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1c19b-113">Attributes</span></span>  
  
|<span data-ttu-id="1c19b-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="1c19b-114">Attribute</span></span>|<span data-ttu-id="1c19b-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1c19b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c19b-116">type</span><span class="sxs-lookup"><span data-stu-id="1c19b-116">type</span></span>|<span data-ttu-id="1c19b-117">Určuje typ překládání tokenu služby.</span><span class="sxs-lookup"><span data-stu-id="1c19b-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="1c19b-118"><xref:System.IdentityModel.Selectors.SecurityTokenResolver> Typ nebo typ, který je <xref:System.IdentityModel.Selectors.SecurityTokenResolver> odvozen z třídy.</span><span class="sxs-lookup"><span data-stu-id="1c19b-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="1c19b-119">Další informace o tom, `type` jak zadat atribut, naleznete v tématu [Vlastní odkazy typu].</span><span class="sxs-lookup"><span data-stu-id="1c19b-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="1c19b-120">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="1c19b-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c19b-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1c19b-121">Child Elements</span></span>  
 <span data-ttu-id="1c19b-122">Žádný</span><span class="sxs-lookup"><span data-stu-id="1c19b-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c19b-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1c19b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1c19b-124">Element</span><span class="sxs-lookup"><span data-stu-id="1c19b-124">Element</span></span>|<span data-ttu-id="1c19b-125">Popis</span><span class="sxs-lookup"><span data-stu-id="1c19b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c19b-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="1c19b-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="1c19b-127">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1c19b-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c19b-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c19b-128">Remarks</span></span>  
 <span data-ttu-id="1c19b-129">Překládání tokenů služby lze vyřešit šifrovací token na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="1c19b-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="1c19b-130">Používá se k načtení klíče, který by měl být použit k dešifrování příchozích tokenů.</span><span class="sxs-lookup"><span data-stu-id="1c19b-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="1c19b-131">Je nutné `type` zadat atribut.</span><span class="sxs-lookup"><span data-stu-id="1c19b-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="1c19b-132">Zadaný typ může <xref:System.IdentityModel.Selectors.SecurityTokenResolver> být buď nebo vlastní <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typ, který je odvozen z třídy.</span><span class="sxs-lookup"><span data-stu-id="1c19b-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="1c19b-133">Některé obslužné rutiny tokenů umožňují určit nastavení překladače tokenů služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="1c19b-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="1c19b-134">Nastavení na obslužné rutiny jednotlivých tokenů přepsat ty zadané v kolekci obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1c19b-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c19b-135">Určení `<serviceTokenResolver>` prvku jako podřízeného prvku [ \<identityKonfigurace>](identityconfiguration.md) element ubírala, ale je stále podporována z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="1c19b-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="1c19b-136">Nastavení na `<securityTokenHandlerConfiguration>` prvek přepsat ty `<identityConfiguration>` na prvek.</span><span class="sxs-lookup"><span data-stu-id="1c19b-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c19b-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c19b-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
