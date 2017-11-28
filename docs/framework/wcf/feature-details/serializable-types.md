---
title: "Serializovatelné typy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f053edc688080293b6fae927049bf6776551b7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="serializable-types"></a><span data-ttu-id="8f0e2-102">Serializovatelné typy</span><span class="sxs-lookup"><span data-stu-id="8f0e2-102">Serializable Types</span></span>
<span data-ttu-id="8f0e2-103">Ve výchozím nastavení <xref:System.Runtime.Serialization.DataContractSerializer> serializuje všechny typy veřejně viditelný.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-103">By default, the <xref:System.Runtime.Serialization.DataContractSerializer> serializes all publicly visible types.</span></span> <span data-ttu-id="8f0e2-104">Všechny veřejné vlastnosti a pole typu se serializují.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-104">All public read/write properties and fields of the type are serialized.</span></span>  
  
 <span data-ttu-id="8f0e2-105">Můžete změnit výchozí chování použitím <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy typy a členy této funkce může být užitečné v situacích, kdy máte typy, které nejsou ve vaší kontrole a nemůže být upraven k přidání atributů.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-105">You can change the default behavior by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the types and members This feature can be useful in situations in which you have types that are not under your control and cannot be modified to add attributes.</span></span> <span data-ttu-id="8f0e2-106"><xref:System.Runtime.Serialization.DataContractSerializer> Rozpozná takové "Zrušit označení" typy.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-106">The <xref:System.Runtime.Serialization.DataContractSerializer> recognizes such "unmarked" types.</span></span>  
  
## <a name="serialization-defaults"></a><span data-ttu-id="8f0e2-107">Výchozí serializace</span><span class="sxs-lookup"><span data-stu-id="8f0e2-107">Serialization Defaults</span></span>  
 <span data-ttu-id="8f0e2-108">Můžete použít <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy explicitně řízení nebo upravit serializaci typů a členů.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-108">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to explicitly control or customize the serialization of types and members.</span></span> <span data-ttu-id="8f0e2-109">Kromě toho můžete použít tyto atributy pro soukromá pole.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-109">In addition, you can apply these attributes to private fields.</span></span> <span data-ttu-id="8f0e2-110">I typy, které nejsou označené jako tyto atributy se však serializovat a deserializovat.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-110">However, even types that are not marked with these attributes are serialized and deserialized.</span></span> <span data-ttu-id="8f0e2-111">Platí následující pravidla a výjimky:</span><span class="sxs-lookup"><span data-stu-id="8f0e2-111">The following rules and exceptions apply:</span></span>  
  
-   <span data-ttu-id="8f0e2-112"><xref:System.Runtime.Serialization.DataContractSerializer> Odvodí kontraktu dat z typů bez atributů s použitím výchozí vlastnosti nově vytvořený typů.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-112">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract from types without attributes using the default properties of the newly created types.</span></span>  
  
-   <span data-ttu-id="8f0e2-113">Všechny veřejné polí a vlastností s veřejnou `get` a `set` se serializují metody, pokud použijete <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atribut tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-113">All public fields, and properties with public `get` and `set` methods are serialized, unless you apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
-   <span data-ttu-id="8f0e2-114">Sémantika serializace je podobné jako u <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-114">The serialization semantics are similar to those of the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
-   <span data-ttu-id="8f0e2-115">Zrušit označení typy jsou serializovat pouze veřejné typů pomocí konstruktorů, které nemají parametry.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-115">In unmarked types, only public types with constructors that do not have parameters are serialized.</span></span> <span data-ttu-id="8f0e2-116">Výjimka, která má toto pravidlo je <xref:System.Runtime.Serialization.ExtensionDataObject> použít s <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-116">The exception to this rule is <xref:System.Runtime.Serialization.ExtensionDataObject> used with the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span>  
  
-   <span data-ttu-id="8f0e2-117">Pole jen pro čtení, vlastnosti bez `get` nebo `set` metody a vlastnosti s interní nebo privátní `set` nebo `get` nejsou serializované metody.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-117">Read-only fields, properties without a `get` or `set` method, and properties with internal or private `set` or `get` methods are not serialized.</span></span> <span data-ttu-id="8f0e2-118">Tyto vlastnosti jsou ignorovány a nedojde k výjimce, s výjimkou pouze pro získání kolekce.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-118">Such properties are ignored and no exception is thrown, except in the case of get-only collections.</span></span>  
  
-   <span data-ttu-id="8f0e2-119"><xref:System.Xml.Serialization.XmlSerializer>atributy (například `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`a tak dále) jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-119"><xref:System.Xml.Serialization.XmlSerializer> attributes (such as `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`, and so on) are ignored.</span></span>  
  
-   <span data-ttu-id="8f0e2-120">Pokud se nevztahují <xref:System.Runtime.Serialization.DataContractAttribute> atribut k danému typu serializátor ignoruje kteréhokoli člena v tomto typu, ke kterému <xref:System.Runtime.Serialization.DataMemberAttribute> atribut se používá.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-120">If you do not apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a given type, the serializer ignores any member in that type to which the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute is applied.</span></span>  
  
-   <span data-ttu-id="8f0e2-121"><xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> Vlastnost je podporována v typech neoznačené <xref:System.Runtime.Serialization.DataContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-121">The <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> property is supported in types not marked with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute.</span></span> <span data-ttu-id="8f0e2-122">To zahrnuje podporu pro <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut na neoznačených typy.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-122">This includes support for the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on unmarked types.</span></span>  
  
-   <span data-ttu-id="8f0e2-123">Chcete-li "chodit" procesu serializace pro veřejné členy, vlastnosti nebo pole, použít <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atribut tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-123">To "opt out" of the serialization process for public members, properties, or fields, apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="8f0e2-124">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="8f0e2-124">Inheritance</span></span>  
 <span data-ttu-id="8f0e2-125">Zrušit označení typy (typy bez <xref:System.Runtime.Serialization.DataContractAttribute> atribut) může dědit vlastnosti z typů, které mají tento atribut; však není povoleno naopak: typy s atributem nelze zrušit označení typy dědí.</span><span class="sxs-lookup"><span data-stu-id="8f0e2-125">Unmarked types (types without the <xref:System.Runtime.Serialization.DataContractAttribute> attribute) can inherit from types that do have this attribute; however, the reverse is not permitted: types with the attribute cannot inherit from unmarked types.</span></span> <span data-ttu-id="8f0e2-126">Toto pravidlo se vynucuje hlavně kvůli zajištění zpětné kompatibility s kód napsaný v dřívějších verzích [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f0e2-126">This rule is enforced primarily to ensure backward compatibility with code written in earlier versions of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f0e2-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f0e2-127">See Also</span></span>  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="8f0e2-128">Typy podporované systémem serializátor kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="8f0e2-128">Types Supported by the Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
