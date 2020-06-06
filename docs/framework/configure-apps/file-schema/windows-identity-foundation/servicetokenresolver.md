---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152577"
---
# \<serviceTokenResolver>
<span data-ttu-id="04a46-101">Registruje překladač tokenů služby, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="04a46-101">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="04a46-102">Překladač tokenů služby se používá k překladu šifrovacího tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="04a46-102">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="04a46-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04a46-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04a46-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="04a46-104">Attributes and Elements</span></span>  
 <span data-ttu-id="04a46-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="04a46-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04a46-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="04a46-106">Attributes</span></span>  
  
|<span data-ttu-id="04a46-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="04a46-107">Attribute</span></span>|<span data-ttu-id="04a46-108">Popis</span><span class="sxs-lookup"><span data-stu-id="04a46-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04a46-109">typ</span><span class="sxs-lookup"><span data-stu-id="04a46-109">type</span></span>|<span data-ttu-id="04a46-110">Určuje typ překladače tokenu služby.</span><span class="sxs-lookup"><span data-stu-id="04a46-110">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="04a46-111">Buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typ, nebo typ, který je odvozen od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="04a46-111">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="04a46-112">Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="04a46-112">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="04a46-113">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="04a46-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04a46-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="04a46-114">Child Elements</span></span>  
 <span data-ttu-id="04a46-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="04a46-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04a46-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="04a46-116">Parent Elements</span></span>  
  
|<span data-ttu-id="04a46-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="04a46-117">Element</span></span>|<span data-ttu-id="04a46-118">Description</span><span class="sxs-lookup"><span data-stu-id="04a46-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="04a46-119">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="04a46-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04a46-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04a46-120">Remarks</span></span>  
 <span data-ttu-id="04a46-121">Překladač tokenů služby se dá použít k vyřešení šifrovacího tokenu u příchozích tokenů a zpráv.</span><span class="sxs-lookup"><span data-stu-id="04a46-121">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="04a46-122">Používá se k načtení klíče, který by se měl použít k dešifrování příchozích tokenů.</span><span class="sxs-lookup"><span data-stu-id="04a46-122">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="04a46-123">Je nutné zadat `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="04a46-123">You must specify the `type` attribute.</span></span> <span data-ttu-id="04a46-124">Zadaný typ může být buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> nebo vlastní typ, který je odvozen od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="04a46-124">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="04a46-125">Některé obslužné rutiny tokenů umožňují zadat nastavení překladače tokenu služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="04a46-125">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="04a46-126">Nastavení pro obslužné rutiny jednotlivých tokenů přepíší ty zadané v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="04a46-126">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04a46-127">Určení `<serviceTokenResolver>` prvku jako podřízený element [\<identityConfiguration>](identityconfiguration.md) elementu je zastaralé, ale je stále podporováno z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="04a46-127">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="04a46-128">Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="04a46-128">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04a46-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="04a46-129">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
