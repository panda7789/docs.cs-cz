---
title: Schéma kontraktů dat – referenční informace
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: 04d1f753e5788460404942a21a29e1612f674e90
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593565"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="66588-102">Schéma kontraktů dat – referenční informace</span><span class="sxs-lookup"><span data-stu-id="66588-102">Data Contract Schema Reference</span></span>

<span data-ttu-id="66588-103">Toto téma popisuje podmnožinu schématu XML (XSD) používaného <xref:System.Runtime.Serialization.DataContractSerializer> pro popis typů modulu CLR (Common Language Runtime) pro serializaci XML.</span><span class="sxs-lookup"><span data-stu-id="66588-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>

## <a name="datacontractserializer-mappings"></a><span data-ttu-id="66588-104">Mapování DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="66588-104">DataContractSerializer Mappings</span></span>

<span data-ttu-id="66588-105">`DataContractSerializer`Mapuje typy CLR na XSD při exportu metadat ze služby Windows Communication Foundation (WCF) pomocí koncového bodu metadat nebo nástroje pro tvorbu [metadat ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="66588-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="66588-106">Další informace najdete v tématu [serializátor kontraktu dat](data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="66588-106">For more information, see [Data Contract Serializer](data-contract-serializer.md).</span></span>

<span data-ttu-id="66588-107">`DataContractSerializer`Také MAPUJE XSD na typy CLR, pokud se Svcutil. exe používá pro přístup k dokumentům WSDL (Web Services Description Language) nebo XSD a k vygenerování kontraktů dat pro služby nebo klienty.</span><span class="sxs-lookup"><span data-stu-id="66588-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>

<span data-ttu-id="66588-108">Pouze instance schématu XML, které odpovídají požadavkům uvedeným v tomto dokumentu, lze namapovat na typy CLR pomocí `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="66588-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>

### <a name="support-levels"></a><span data-ttu-id="66588-109">Úrovně podpory</span><span class="sxs-lookup"><span data-stu-id="66588-109">Support Levels</span></span>

<span data-ttu-id="66588-110">`DataContractSerializer`Poskytuje následující úrovně podpory pro danou funkci schématu XML:</span><span class="sxs-lookup"><span data-stu-id="66588-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>

- <span data-ttu-id="66588-111">**Podporuje**se.</span><span class="sxs-lookup"><span data-stu-id="66588-111">**Supported**.</span></span> <span data-ttu-id="66588-112">Existuje explicitní mapování z této funkce na typy CLR nebo atributy (nebo obojí) pomocí `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="66588-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>

- <span data-ttu-id="66588-113">**Ignoruje**se.</span><span class="sxs-lookup"><span data-stu-id="66588-113">**Ignored**.</span></span> <span data-ttu-id="66588-114">Tato funkce je povolena v schématech importovaných `DataContractSerializer` , ale nemá žádný vliv na generování kódu.</span><span class="sxs-lookup"><span data-stu-id="66588-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>

- <span data-ttu-id="66588-115">**Zakázané**.</span><span class="sxs-lookup"><span data-stu-id="66588-115">**Forbidden**.</span></span> <span data-ttu-id="66588-116">Nástroj nepodporuje `DataContractSerializer` Import schématu pomocí funkce.</span><span class="sxs-lookup"><span data-stu-id="66588-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="66588-117">Například Svcutil. exe při přístupu k WSDL se schématem, které tuto funkci používá, se vrátí k použití <xref:System.Xml.Serialization.XmlSerializer> namísto.</span><span class="sxs-lookup"><span data-stu-id="66588-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="66588-118">Toto je ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="66588-118">This is by default.</span></span>

## <a name="general-information"></a><span data-ttu-id="66588-119">Obecné informace</span><span class="sxs-lookup"><span data-stu-id="66588-119">General Information</span></span>

- <span data-ttu-id="66588-120">Obor názvů schématu je popsán ve [schématu XML](https://www.w3.org/2001/XMLSchema).</span><span class="sxs-lookup"><span data-stu-id="66588-120">The schema namespace is described at [XML Schema](https://www.w3.org/2001/XMLSchema).</span></span> <span data-ttu-id="66588-121">V tomto dokumentu je použita předpona "XS".</span><span class="sxs-lookup"><span data-stu-id="66588-121">The prefix "xs" is used in this document.</span></span>

- <span data-ttu-id="66588-122">Všechny atributy s oborem názvů bez schématu jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="66588-122">Any attributes with a non-schema namespace are ignored.</span></span>

- <span data-ttu-id="66588-123">Jakékoli poznámky (kromě těch, které jsou popsány v tomto dokumentu) se ignorují.</span><span class="sxs-lookup"><span data-stu-id="66588-123">Any annotations (except for those described in this document) are ignored.</span></span>

### <a name="xsschema-attributes"></a><span data-ttu-id="66588-124">\<xs:schema>: atributy</span><span class="sxs-lookup"><span data-stu-id="66588-124">\<xs:schema>: attributes</span></span>

|<span data-ttu-id="66588-125">Atribut</span><span class="sxs-lookup"><span data-stu-id="66588-125">Attribute</span></span>|<span data-ttu-id="66588-126">Kontraktu DataContract</span><span class="sxs-lookup"><span data-stu-id="66588-126">DataContract</span></span>|
|---------------|------------------|
|`attributeFormDefault`|<span data-ttu-id="66588-127">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-127">Ignored.</span></span>|
|`blockDefault`|<span data-ttu-id="66588-128">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-128">Ignored.</span></span>|
|`elementFormDefault`|<span data-ttu-id="66588-129">Musí být kvalifikován.</span><span class="sxs-lookup"><span data-stu-id="66588-129">Must be qualified.</span></span> <span data-ttu-id="66588-130">Všechny elementy musí být kvalifikovány, aby bylo schéma podporováno nástrojem `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="66588-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="66588-131">To lze provést buď nastavením xs:schema/@elementFormDefault na "kvalifikovaný", nebo nastavením xs:element/@form na "kvalifikovaný" pro každou deklaraci jednotlivého prvku.</span><span class="sxs-lookup"><span data-stu-id="66588-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|
|`finalDefault`|<span data-ttu-id="66588-132">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-132">Ignored.</span></span>|
|`Id`|<span data-ttu-id="66588-133">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-133">Ignored.</span></span>|
|`targetNamespace`|<span data-ttu-id="66588-134">Podporováno a mapováno na obor názvů kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="66588-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="66588-135">Pokud tento atribut není zadán, je použit prázdný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="66588-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="66588-136">Nemůže se jednat o vyhrazený obor názvů `http://schemas.microsoft.com/2003/10/Serialization/` .</span><span class="sxs-lookup"><span data-stu-id="66588-136">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|
|`version`|<span data-ttu-id="66588-137">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-137">Ignored.</span></span>|

### <a name="xsschema-contents"></a><span data-ttu-id="66588-138">\<xs:schema>: obsah</span><span class="sxs-lookup"><span data-stu-id="66588-138">\<xs:schema>: contents</span></span>

|<span data-ttu-id="66588-139">Obsah</span><span class="sxs-lookup"><span data-stu-id="66588-139">Contents</span></span>|<span data-ttu-id="66588-140">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-140">Schema</span></span>|
|--------------|------------|
|`include`|<span data-ttu-id="66588-141">Podporuje se.</span><span class="sxs-lookup"><span data-stu-id="66588-141">Supported.</span></span> <span data-ttu-id="66588-142">`DataContractSerializer`podporuje xs: include a xs: import.</span><span class="sxs-lookup"><span data-stu-id="66588-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="66588-143">Svcutil. exe však omezuje následující `xs:include/@schemaLocation` a `xs:import/@location` odkazy na to, kdy jsou metadata načtena z místního souboru.</span><span class="sxs-lookup"><span data-stu-id="66588-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="66588-144">Seznam souborů schématu musí být předán pomocí mechanismu mimo pásmo, a ne prostřednictvím `include` v tomto případě. `include` dokumenty schématu d se ignorují.</span><span class="sxs-lookup"><span data-stu-id="66588-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`redefine`|<span data-ttu-id="66588-145">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-145">Forbidden.</span></span> <span data-ttu-id="66588-146">Z `xs:redefine` bezpečnostních důvodů je použití zakázáno z `DataContractSerializer` důvodu zabezpečení: `x:redefine` vyžaduje, `schemaLocation` aby následovala.</span><span class="sxs-lookup"><span data-stu-id="66588-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="66588-147">Za určitých okolností Svcutil. exe využívající DataContract omezí použití `schemaLocation` .</span><span class="sxs-lookup"><span data-stu-id="66588-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|
|`import`|<span data-ttu-id="66588-148">Podporuje se.</span><span class="sxs-lookup"><span data-stu-id="66588-148">Supported.</span></span> <span data-ttu-id="66588-149">`DataContractSerializer`podporuje `xs:include` a `xs:import` .</span><span class="sxs-lookup"><span data-stu-id="66588-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="66588-150">Svcutil. exe však omezuje následující `xs:include/@schemaLocation` a `xs:import/@location` odkazy na to, kdy jsou metadata načtena z místního souboru.</span><span class="sxs-lookup"><span data-stu-id="66588-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="66588-151">Seznam souborů schématu musí být předán pomocí mechanismu mimo pásmo, a ne prostřednictvím `include` v tomto případě. `include` dokumenty schématu d se ignorují.</span><span class="sxs-lookup"><span data-stu-id="66588-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`simpleType`|<span data-ttu-id="66588-152">Podporuje se.</span><span class="sxs-lookup"><span data-stu-id="66588-152">Supported.</span></span> <span data-ttu-id="66588-153">Přečtěte si část `xs:simpleType`.</span><span class="sxs-lookup"><span data-stu-id="66588-153">See the `xs:simpleType` section.</span></span>|
|`complexType`|<span data-ttu-id="66588-154">Podporováno, mapuje se na kontrakty dat.</span><span class="sxs-lookup"><span data-stu-id="66588-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="66588-155">Přečtěte si část `xs:complexType`.</span><span class="sxs-lookup"><span data-stu-id="66588-155">See the `xs:complexType` section.</span></span>|
|`group`|<span data-ttu-id="66588-156">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-156">Ignored.</span></span> <span data-ttu-id="66588-157">`DataContractSerializer`nepodporuje použití `xs:group` , `xs:attributeGroup` , a `xs:attribute` .</span><span class="sxs-lookup"><span data-stu-id="66588-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="66588-158">Tato deklarace jsou ignorována jako podřízené položky `xs:schema` , ale nelze na ni odkazovat v rámci `complexType` nebo jiných podporovaných konstrukcích.</span><span class="sxs-lookup"><span data-stu-id="66588-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`attributeGroup`|<span data-ttu-id="66588-159">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-159">Ignored.</span></span> <span data-ttu-id="66588-160">`DataContractSerializer`nepodporuje použití `xs:group` , `xs:attributeGroup` , a `xs:attribute` .</span><span class="sxs-lookup"><span data-stu-id="66588-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="66588-161">Tato deklarace jsou ignorována jako podřízené položky `xs:schema` , ale nelze na ni odkazovat v rámci `complexType` nebo jiných podporovaných konstrukcích.</span><span class="sxs-lookup"><span data-stu-id="66588-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`element`|<span data-ttu-id="66588-162">Podporuje se.</span><span class="sxs-lookup"><span data-stu-id="66588-162">Supported.</span></span> <span data-ttu-id="66588-163">Viz deklarace globálních elementů (připravený).</span><span class="sxs-lookup"><span data-stu-id="66588-163">See Global Element Declaration (GED).</span></span>|
|`attribute`|<span data-ttu-id="66588-164">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-164">Ignored.</span></span> <span data-ttu-id="66588-165">`DataContractSerializer`nepodporuje použití `xs:group` , `xs:attributeGroup` , a `xs:attribute` .</span><span class="sxs-lookup"><span data-stu-id="66588-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="66588-166">Tato deklarace jsou ignorována jako podřízené položky `xs:schema` , ale nelze na ni odkazovat v rámci `complexType` nebo jiných podporovaných konstrukcích.</span><span class="sxs-lookup"><span data-stu-id="66588-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`notation`|<span data-ttu-id="66588-167">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-167">Ignored.</span></span>|

## <a name="complex-types--xscomplextype"></a><span data-ttu-id="66588-168">Komplexní typy –\<xs:complexType></span><span class="sxs-lookup"><span data-stu-id="66588-168">Complex Types – \<xs:complexType></span></span>

### <a name="general-information"></a><span data-ttu-id="66588-169">Obecné informace</span><span class="sxs-lookup"><span data-stu-id="66588-169">General Information</span></span>

<span data-ttu-id="66588-170">Každý komplexní typ \<xs:complexType> se mapuje na kontrakt dat.</span><span class="sxs-lookup"><span data-stu-id="66588-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>

### <a name="xscomplextype-attributes"></a><span data-ttu-id="66588-171">\<xs:complexType>: atributy</span><span class="sxs-lookup"><span data-stu-id="66588-171">\<xs:complexType>: attributes</span></span>

|<span data-ttu-id="66588-172">Atribut</span><span class="sxs-lookup"><span data-stu-id="66588-172">Attribute</span></span>|<span data-ttu-id="66588-173">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-173">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="66588-174">Hodnota musí být false (výchozí).</span><span class="sxs-lookup"><span data-stu-id="66588-174">Must be false (default).</span></span>|
|`block`|<span data-ttu-id="66588-175">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-175">Forbidden.</span></span>|
|`final`|<span data-ttu-id="66588-176">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-176">Ignored.</span></span>|
|`id`|<span data-ttu-id="66588-177">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-177">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="66588-178">Hodnota musí být false (výchozí).</span><span class="sxs-lookup"><span data-stu-id="66588-178">Must be false (default).</span></span>|
|`name`|<span data-ttu-id="66588-179">Podporováno a mapováno na název kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="66588-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="66588-180">Pokud v názvu existují tečky, je proveden pokus o mapování typu na vnitřní typ.</span><span class="sxs-lookup"><span data-stu-id="66588-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="66588-181">Například komplexní typ nazvaný `A.B` mapuje typ kontraktu dat, který je vnitřní typ typu s názvem kontraktu dat `A` , ale pouze v případě, že takový typ kontraktu dat existuje.</span><span class="sxs-lookup"><span data-stu-id="66588-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="66588-182">Je možné použít více než jednu úroveň vnoření: `A.B.C` může to být například vnitřní typ, ale pouze pokud `A` `A.B` existuje.</span><span class="sxs-lookup"><span data-stu-id="66588-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|

### <a name="xscomplextype-contents"></a><span data-ttu-id="66588-183">\<xs:complexType>: obsah</span><span class="sxs-lookup"><span data-stu-id="66588-183">\<xs:complexType>: contents</span></span>

|<span data-ttu-id="66588-184">Obsah</span><span class="sxs-lookup"><span data-stu-id="66588-184">Contents</span></span>|<span data-ttu-id="66588-185">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-185">Schema</span></span>|
|--------------|------------|
|`simpleContent`|<span data-ttu-id="66588-186">Rozšíření jsou zakázána.</span><span class="sxs-lookup"><span data-stu-id="66588-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="66588-187">Omezení je povoleno pouze z `anySimpleType` .</span><span class="sxs-lookup"><span data-stu-id="66588-187">Restriction is allowed only from `anySimpleType`.</span></span>|
|`complexContent`|<span data-ttu-id="66588-188">Podporuje se.</span><span class="sxs-lookup"><span data-stu-id="66588-188">Supported.</span></span> <span data-ttu-id="66588-189">Viz "dědičnost".</span><span class="sxs-lookup"><span data-stu-id="66588-189">See "Inheritance".</span></span>|
|`group`|<span data-ttu-id="66588-190">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-190">Forbidden.</span></span>|
|`all`|<span data-ttu-id="66588-191">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-191">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="66588-192">Forbidden</span><span class="sxs-lookup"><span data-stu-id="66588-192">Forbidden</span></span>|
|`sequence`|<span data-ttu-id="66588-193">Podporováno, mapuje se na datové členy kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="66588-193">Supported, maps to data members of a data contract.</span></span>|
|`attribute`|<span data-ttu-id="66588-194">Zakázáno, i když use = "zakázáno" (s jednou výjimkou).</span><span class="sxs-lookup"><span data-stu-id="66588-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="66588-195">Jsou podporovány pouze volitelné atributy z oboru názvů schématu standardní serializace.</span><span class="sxs-lookup"><span data-stu-id="66588-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="66588-196">Nemapují se na datové členy v programovacím modelu kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="66588-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="66588-197">V současné době pouze jeden takový atribut má význam a je popsán v oddílu ISerializable.</span><span class="sxs-lookup"><span data-stu-id="66588-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="66588-198">Všechny ostatní jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="66588-198">All others are ignored.</span></span>|
|`attributeGroup`|<span data-ttu-id="66588-199">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-199">Forbidden.</span></span> <span data-ttu-id="66588-200">Ve verzi WCF v1 `DataContractSerializer` ignoruje přítomnost `attributeGroup` uvnitř `xs:complexType` .</span><span class="sxs-lookup"><span data-stu-id="66588-200">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|
|`anyAttribute`|<span data-ttu-id="66588-201">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-201">Forbidden.</span></span>|
|<span data-ttu-id="66588-202">obsahovat</span><span class="sxs-lookup"><span data-stu-id="66588-202">(empty)</span></span>|<span data-ttu-id="66588-203">Mapuje se na kontrakt dat bez datových členů.</span><span class="sxs-lookup"><span data-stu-id="66588-203">Maps to a data contract with no data members.</span></span>|

### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="66588-204">\<xs:sequence>ve komplexním typu: atributy</span><span class="sxs-lookup"><span data-stu-id="66588-204">\<xs:sequence> in a complex type: attributes</span></span>

|<span data-ttu-id="66588-205">Atribut</span><span class="sxs-lookup"><span data-stu-id="66588-205">Attribute</span></span>|<span data-ttu-id="66588-206">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-206">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="66588-207">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-207">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="66588-208">Musí mít hodnotu 1 (výchozí).</span><span class="sxs-lookup"><span data-stu-id="66588-208">Must be 1 (default).</span></span>|
|`minOccurs`|<span data-ttu-id="66588-209">Musí mít hodnotu 1 (výchozí).</span><span class="sxs-lookup"><span data-stu-id="66588-209">Must be 1 (default).</span></span>|

### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="66588-210">\<xs:sequence>v komplexním typu: obsah</span><span class="sxs-lookup"><span data-stu-id="66588-210">\<xs:sequence> in a complex type: contents</span></span>

|<span data-ttu-id="66588-211">Obsah</span><span class="sxs-lookup"><span data-stu-id="66588-211">Contents</span></span>|<span data-ttu-id="66588-212">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-212">Schema</span></span>|
|--------------|------------|
|`element`|<span data-ttu-id="66588-213">Každá instance se mapuje na datový člen.</span><span class="sxs-lookup"><span data-stu-id="66588-213">Each instance maps to a data member.</span></span>|
|`group`|<span data-ttu-id="66588-214">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-214">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="66588-215">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-215">Forbidden.</span></span>|
|`sequence`|<span data-ttu-id="66588-216">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-216">Forbidden.</span></span>|
|`any`|<span data-ttu-id="66588-217">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-217">Forbidden.</span></span>|
|<span data-ttu-id="66588-218">obsahovat</span><span class="sxs-lookup"><span data-stu-id="66588-218">(empty)</span></span>|<span data-ttu-id="66588-219">Mapuje se na kontrakt dat bez datových členů.</span><span class="sxs-lookup"><span data-stu-id="66588-219">Maps to a data contract with no data members.</span></span>|

## <a name="elements--xselement"></a><span data-ttu-id="66588-220">Elementu\<xs:element></span><span class="sxs-lookup"><span data-stu-id="66588-220">Elements – \<xs:element></span></span>

### <a name="general-information"></a><span data-ttu-id="66588-221">Obecné informace</span><span class="sxs-lookup"><span data-stu-id="66588-221">General Information</span></span>

<span data-ttu-id="66588-222">`<xs:element>`může dojít v následujících kontextech:</span><span class="sxs-lookup"><span data-stu-id="66588-222">`<xs:element>` can occur in the following contexts:</span></span>

- <span data-ttu-id="66588-223">Může k tomu dojít v rámci `<xs:sequence>` , který popisuje datový člen pravidelného kontraktu dat (bez kolekce).</span><span class="sxs-lookup"><span data-stu-id="66588-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="66588-224">V takovém případě `maxOccurs` musí být atribut 1.</span><span class="sxs-lookup"><span data-stu-id="66588-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="66588-225">(Hodnota 0 není povolená).</span><span class="sxs-lookup"><span data-stu-id="66588-225">(A value of 0 is not allowed).</span></span>

- <span data-ttu-id="66588-226">Může k tomu dojít v rámci `<xs:sequence>` , který popisuje datový člen kontraktu dat kolekce.</span><span class="sxs-lookup"><span data-stu-id="66588-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="66588-227">V tomto případě `maxOccurs` musí být atribut větší než 1 nebo "Unbounded".</span><span class="sxs-lookup"><span data-stu-id="66588-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>

- <span data-ttu-id="66588-228">Může se vyskytnout v rámci `<xs:schema>` deklarace jako globální element (připravený).</span><span class="sxs-lookup"><span data-stu-id="66588-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="66588-229">\<xs:element>s hodnota atributu maxOccurs = 1 v rámci \<xs:sequence> (datové členy)</span><span class="sxs-lookup"><span data-stu-id="66588-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>

|<span data-ttu-id="66588-230">Atribut</span><span class="sxs-lookup"><span data-stu-id="66588-230">Attribute</span></span>|<span data-ttu-id="66588-231">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-231">Schema</span></span>|
|---------------|------------|
|`ref`|<span data-ttu-id="66588-232">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-232">Forbidden.</span></span>|
|`name`|<span data-ttu-id="66588-233">Podporováno, mapuje se na název datového členu.</span><span class="sxs-lookup"><span data-stu-id="66588-233">Supported, maps to the data member name.</span></span>|
|`type`|<span data-ttu-id="66588-234">Podporováno, je mapováno na typ datového člena.</span><span class="sxs-lookup"><span data-stu-id="66588-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="66588-235">Další informace naleznete v tématu mapování typů a primitivních hodnot.</span><span class="sxs-lookup"><span data-stu-id="66588-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="66588-236">Pokud není zadán (a element neobsahuje anonymní typ), `xs:anyType` předpokládá se.</span><span class="sxs-lookup"><span data-stu-id="66588-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|
|`block`|<span data-ttu-id="66588-237">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-237">Ignored.</span></span>|
|`default`|<span data-ttu-id="66588-238">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-238">Forbidden.</span></span>|
|`fixed`|<span data-ttu-id="66588-239">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-239">Forbidden.</span></span>|
|`form`|<span data-ttu-id="66588-240">Musí být kvalifikován.</span><span class="sxs-lookup"><span data-stu-id="66588-240">Must be qualified.</span></span> <span data-ttu-id="66588-241">Tento atribut lze nastavit pomocí `elementFormDefault` `xs:schema` .</span><span class="sxs-lookup"><span data-stu-id="66588-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|
|`id`|<span data-ttu-id="66588-242">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-242">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="66588-243">1</span><span class="sxs-lookup"><span data-stu-id="66588-243">1</span></span>|
|`minOccurs`|<span data-ttu-id="66588-244">Mapuje se na <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost datového členu ( `IsRequired` true, pokud `minOccurs` je hodnota 1).</span><span class="sxs-lookup"><span data-stu-id="66588-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|
|`nillable`|<span data-ttu-id="66588-245">Má vliv na mapování typů.</span><span class="sxs-lookup"><span data-stu-id="66588-245">Affects type mapping.</span></span> <span data-ttu-id="66588-246">Viz mapování typů a primitivních hodnot.</span><span class="sxs-lookup"><span data-stu-id="66588-246">See Type/primitive mapping.</span></span>|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="66588-247">\<xs:element>s maxOccurs>1 v rámci \<xs:sequence> (kolekcí)</span><span class="sxs-lookup"><span data-stu-id="66588-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>

- <span data-ttu-id="66588-248">Provede mapování na <xref:System.Runtime.Serialization.CollectionDataContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="66588-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>

- <span data-ttu-id="66588-249">V typech kolekcí je povolena pouze jedna xs: element v rámci typu xs: Sequence.</span><span class="sxs-lookup"><span data-stu-id="66588-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>

 <span data-ttu-id="66588-250">Kolekce mohou mít následující typy:</span><span class="sxs-lookup"><span data-stu-id="66588-250">Collections can be of the following types:</span></span>

- <span data-ttu-id="66588-251">Běžné kolekce (například pole).</span><span class="sxs-lookup"><span data-stu-id="66588-251">Regular collections (for example, arrays).</span></span>

- <span data-ttu-id="66588-252">Kolekce slovníku (mapování jedné hodnoty na jinou, například a <xref:System.Collections.Hashtable> ).</span><span class="sxs-lookup"><span data-stu-id="66588-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>

- <span data-ttu-id="66588-253">Jediný rozdíl mezi slovníkem a polem typu dvojice klíč/hodnota je ve vygenerovaném programovacím modelu.</span><span class="sxs-lookup"><span data-stu-id="66588-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="66588-254">Existuje mechanismus pro anotaci schématu, který lze použít k označení toho, že daný typ je kolekce slovníku.</span><span class="sxs-lookup"><span data-stu-id="66588-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>

<span data-ttu-id="66588-255">Pravidla pro `ref` `block` atributy,,, `default` `fixed` , `form` a `id` jsou stejná jako pro případ bez kolekce.</span><span class="sxs-lookup"><span data-stu-id="66588-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="66588-256">Další atributy jsou obsaženy v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="66588-256">Other attributes include those in the following table.</span></span>

|<span data-ttu-id="66588-257">Atribut</span><span class="sxs-lookup"><span data-stu-id="66588-257">Attribute</span></span>|<span data-ttu-id="66588-258">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-258">Schema</span></span>|
|---------------|------------|
|`name`|<span data-ttu-id="66588-259">Podporováno, mapuje na <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> vlastnost v `CollectionDataContractAttribute` atributu.</span><span class="sxs-lookup"><span data-stu-id="66588-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|
|`type`|<span data-ttu-id="66588-260">Podporováno, mapuje na typ uložený v kolekci.</span><span class="sxs-lookup"><span data-stu-id="66588-260">Supported, maps to the type stored in the collection.</span></span>|
|`maxOccurs`|<span data-ttu-id="66588-261">Je větší než 1 nebo "Unbounded".</span><span class="sxs-lookup"><span data-stu-id="66588-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="66588-262">Schéma DC by mělo používat "Unbounded".</span><span class="sxs-lookup"><span data-stu-id="66588-262">The DC schema should use "unbounded".</span></span>|
|`minOccurs`|<span data-ttu-id="66588-263">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-263">Ignored.</span></span>|
|`nillable`|<span data-ttu-id="66588-264">Má vliv na mapování typů.</span><span class="sxs-lookup"><span data-stu-id="66588-264">Affects type mapping.</span></span> <span data-ttu-id="66588-265">Tento atribut se pro kolekce slovníku ignoruje.</span><span class="sxs-lookup"><span data-stu-id="66588-265">This attribute is ignored for dictionary collections.</span></span>|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="66588-266">\<xs:element>v rámci \<xs:schema> deklarace globálních elementů</span><span class="sxs-lookup"><span data-stu-id="66588-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>

- <span data-ttu-id="66588-267">Deklarace globálních elementů (připravený), která má stejný název a obor názvů jako typ ve schématu nebo který definuje anonymní typ uvnitř sebe sama, je označována jako přidružená k typu.</span><span class="sxs-lookup"><span data-stu-id="66588-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>

- <span data-ttu-id="66588-268">Export schématu: přidružená GEDs jsou generována pro každý generovaný typ, jednoduchý i složitý.</span><span class="sxs-lookup"><span data-stu-id="66588-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>

- <span data-ttu-id="66588-269">Deserializace/serializace: přidružená GEDs jsou použita jako kořenové prvky pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="66588-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>

- <span data-ttu-id="66588-270">Import schématu: přidružené GEDs nejsou povinné a jsou ignorovány, pokud následují následující pravidla (Pokud nedefinují typy).</span><span class="sxs-lookup"><span data-stu-id="66588-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>

|<span data-ttu-id="66588-271">Atribut</span><span class="sxs-lookup"><span data-stu-id="66588-271">Attribute</span></span>|<span data-ttu-id="66588-272">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-272">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="66588-273">Pro přidruženou GEDs musí mít hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="66588-273">Must be false for associated GEDs.</span></span>|
|`block`|<span data-ttu-id="66588-274">Zakázáno v přidružených GEDs.</span><span class="sxs-lookup"><span data-stu-id="66588-274">Forbidden in associated GEDs.</span></span>|
|`default`|<span data-ttu-id="66588-275">Zakázáno v přidružených GEDs.</span><span class="sxs-lookup"><span data-stu-id="66588-275">Forbidden in associated GEDs.</span></span>|
|`final`|<span data-ttu-id="66588-276">Pro přidruženou GEDs musí mít hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="66588-276">Must be false for associated GEDs.</span></span>|
|`fixed`|<span data-ttu-id="66588-277">Zakázáno v přidružených GEDs.</span><span class="sxs-lookup"><span data-stu-id="66588-277">Forbidden in associated GEDs.</span></span>|
|`id`|<span data-ttu-id="66588-278">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-278">Ignored.</span></span>|
|`name`|<span data-ttu-id="66588-279">Podporuje se.</span><span class="sxs-lookup"><span data-stu-id="66588-279">Supported.</span></span> <span data-ttu-id="66588-280">Viz definice přidružených GEDs.</span><span class="sxs-lookup"><span data-stu-id="66588-280">See the definition of associated GEDs.</span></span>|
|`nillable`|<span data-ttu-id="66588-281">Pro přidruženou GEDs musí mít hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="66588-281">Must be true for associated GEDs.</span></span>|
|`substitutionGroup`|<span data-ttu-id="66588-282">Zakázáno v přidružených GEDs.</span><span class="sxs-lookup"><span data-stu-id="66588-282">Forbidden in associated GEDs.</span></span>|
|`type`|<span data-ttu-id="66588-283">Podporováno a musí odpovídat přidruženému typu pro přidružené GEDs (Pokud element neobsahuje anonymní typ).</span><span class="sxs-lookup"><span data-stu-id="66588-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|

### <a name="xselement-contents"></a><span data-ttu-id="66588-284">\<xs:element>: obsah</span><span class="sxs-lookup"><span data-stu-id="66588-284">\<xs:element>: contents</span></span>

|<span data-ttu-id="66588-285">Obsah</span><span class="sxs-lookup"><span data-stu-id="66588-285">Contents</span></span>|<span data-ttu-id="66588-286">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-286">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="66588-287">Podporováno. \*</span><span class="sxs-lookup"><span data-stu-id="66588-287">Supported.\*</span></span>|
|`complexType`|<span data-ttu-id="66588-288">Podporováno. \*</span><span class="sxs-lookup"><span data-stu-id="66588-288">Supported.\*</span></span>|
|`unique`|<span data-ttu-id="66588-289">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-289">Ignored.</span></span>|
|`key`|<span data-ttu-id="66588-290">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-290">Ignored.</span></span>|
|`keyref`|<span data-ttu-id="66588-291">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-291">Ignored.</span></span>|
|<span data-ttu-id="66588-292">trhnout</span><span class="sxs-lookup"><span data-stu-id="66588-292">(blank)</span></span>|<span data-ttu-id="66588-293">Podporuje se.</span><span class="sxs-lookup"><span data-stu-id="66588-293">Supported.</span></span>|

<span data-ttu-id="66588-294">\*Při použití `simpleType` a `complexType,` mapování anonymních typů je stejný jako u neanonymních typů s tím rozdílem, že neexistují žádné anonymní kontrakty dat, a proto je vytvořen pojmenovaný kontrakt dat s vygenerovaným názvem odvozeným z názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="66588-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="66588-295">Pravidla pro anonymní typy jsou v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="66588-295">The rules for anonymous types are in the following list:</span></span>

- <span data-ttu-id="66588-296">Podrobnosti implementace WCF: Pokud `xs:element` název neobsahuje tečky, anonymní typ se mapuje na vnitřní typ typu kontraktu s vnějšími daty.</span><span class="sxs-lookup"><span data-stu-id="66588-296">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="66588-297">Pokud název obsahuje tečky, je výsledný typ kontraktu dat nezávislý (nejedná se o vnitřní typ).</span><span class="sxs-lookup"><span data-stu-id="66588-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>

- <span data-ttu-id="66588-298">Název kontraktu generovaných dat vnitřního typu je název kontraktu dat vnějšího typu následovaný tečkou, názvem elementu a řetězcem "typ".</span><span class="sxs-lookup"><span data-stu-id="66588-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>

- <span data-ttu-id="66588-299">Pokud již existuje kontrakt dat s tímto názvem, je název jedinečný připojením "1", "2", "3" a tak dále, dokud nebude vytvořen jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="66588-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>

## <a name="simple-types---xssimpletype"></a><span data-ttu-id="66588-300">Jednoduché typy –\<xs:simpleType></span><span class="sxs-lookup"><span data-stu-id="66588-300">Simple Types - \<xs:simpleType></span></span>

### <a name="xssimpletype-attributes"></a><span data-ttu-id="66588-301">\<xs:simpleType>: atributy</span><span class="sxs-lookup"><span data-stu-id="66588-301">\<xs:simpleType>: attributes</span></span>

|<span data-ttu-id="66588-302">Atribut</span><span class="sxs-lookup"><span data-stu-id="66588-302">Attribute</span></span>|<span data-ttu-id="66588-303">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-303">Schema</span></span>|
|---------------|------------|
|`final`|<span data-ttu-id="66588-304">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-304">Ignored.</span></span>|
|`id`|<span data-ttu-id="66588-305">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-305">Ignored.</span></span>|
|`name`|<span data-ttu-id="66588-306">Podporováno, mapuje se na název kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="66588-306">Supported, maps to the data contract name.</span></span>|

### <a name="xssimpletype-contents"></a><span data-ttu-id="66588-307">\<xs:simpleType>: obsah</span><span class="sxs-lookup"><span data-stu-id="66588-307">\<xs:simpleType>: contents</span></span>

|<span data-ttu-id="66588-308">Obsah</span><span class="sxs-lookup"><span data-stu-id="66588-308">Contents</span></span>|<span data-ttu-id="66588-309">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-309">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="66588-310">Podporuje se.</span><span class="sxs-lookup"><span data-stu-id="66588-310">Supported.</span></span> <span data-ttu-id="66588-311">Mapuje se na kontrakty dat výčtu.</span><span class="sxs-lookup"><span data-stu-id="66588-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="66588-312">Tento atribut je ignorován, pokud neodpovídá vzoru výčtu.</span><span class="sxs-lookup"><span data-stu-id="66588-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="66588-313">Podívejte se na `xs:simpleType` část omezení.</span><span class="sxs-lookup"><span data-stu-id="66588-313">See the `xs:simpleType` restrictions section.</span></span>|
|`list`|<span data-ttu-id="66588-314">Podporuje se.</span><span class="sxs-lookup"><span data-stu-id="66588-314">Supported.</span></span> <span data-ttu-id="66588-315">Provede mapování na označení kontraktů dat výčtu.</span><span class="sxs-lookup"><span data-stu-id="66588-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="66588-316">Viz `xs:simpleType` část seznamy.</span><span class="sxs-lookup"><span data-stu-id="66588-316">See the `xs:simpleType` lists section.</span></span>|
|`union`|<span data-ttu-id="66588-317">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-317">Forbidden.</span></span>|

### \<xs:restriction>

- <span data-ttu-id="66588-318">Omezení komplexního typu jsou podporována pouze pro základní = `xs:anyType` .</span><span class="sxs-lookup"><span data-stu-id="66588-318">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>

- <span data-ttu-id="66588-319">Jednoduchá omezení typu `xs:string` , která nemají žádné charakteristiky omezení jiné než `xs:enumeration` jsou namapovány na kontrakty dat výčtu.</span><span class="sxs-lookup"><span data-stu-id="66588-319">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>

- <span data-ttu-id="66588-320">Všechna ostatní omezení jednoduchých typů jsou namapována na typy, které omezují.</span><span class="sxs-lookup"><span data-stu-id="66588-320">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="66588-321">Například omezení `xs:int` mapování na celé číslo, stejně jako na `xs:int` sebe samé.</span><span class="sxs-lookup"><span data-stu-id="66588-321">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="66588-322">Další informace o mapování primitivního typu najdete v tématu mapování typů a primitivních typů.</span><span class="sxs-lookup"><span data-stu-id="66588-322">For more information about primitive type mapping, see Type/primitive mapping.</span></span>

### <a name="xsrestriction-attributes"></a><span data-ttu-id="66588-323">\<xs:restriction>: atributy</span><span class="sxs-lookup"><span data-stu-id="66588-323">\<xs:restriction>: attributes</span></span>

|<span data-ttu-id="66588-324">Atribut</span><span class="sxs-lookup"><span data-stu-id="66588-324">Attribute</span></span>|<span data-ttu-id="66588-325">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-325">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="66588-326">Musí se jednat o podporovaný jednoduchý typ nebo `xs:anyType` .</span><span class="sxs-lookup"><span data-stu-id="66588-326">Must be a supported simple type or `xs:anyType`.</span></span>|
|`id`|<span data-ttu-id="66588-327">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-327">Ignored.</span></span>|

### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="66588-328">\<xs:restriction>pro všechny ostatní případy: obsah</span><span class="sxs-lookup"><span data-stu-id="66588-328">\<xs:restriction> for all other cases: contents</span></span>

|<span data-ttu-id="66588-329">Obsah</span><span class="sxs-lookup"><span data-stu-id="66588-329">Contents</span></span>|<span data-ttu-id="66588-330">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-330">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="66588-331">Je-li k dispozici, musí být odvozena z podporovaného primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="66588-331">If present, must be derived from a supported primitive type.</span></span>|
|`minExclusive`|<span data-ttu-id="66588-332">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-332">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="66588-333">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-333">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="66588-334">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-334">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="66588-335">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-335">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="66588-336">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-336">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="66588-337">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-337">Ignored.</span></span>|
|`length`|<span data-ttu-id="66588-338">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-338">Ignored.</span></span>|
|`minLength`|<span data-ttu-id="66588-339">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-339">Ignored.</span></span>|
|`maxLength`|<span data-ttu-id="66588-340">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-340">Ignored.</span></span>|
|`enumeration`|<span data-ttu-id="66588-341">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-341">Ignored.</span></span>|
|`whiteSpace`|<span data-ttu-id="66588-342">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-342">Ignored.</span></span>|
|`pattern`|<span data-ttu-id="66588-343">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-343">Ignored.</span></span>|
|<span data-ttu-id="66588-344">trhnout</span><span class="sxs-lookup"><span data-stu-id="66588-344">(blank)</span></span>|<span data-ttu-id="66588-345">Podporuje se.</span><span class="sxs-lookup"><span data-stu-id="66588-345">Supported.</span></span>|

## <a name="enumeration"></a><span data-ttu-id="66588-346">Výčet</span><span class="sxs-lookup"><span data-stu-id="66588-346">Enumeration</span></span>

### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="66588-347">\<xs:restriction>pro výčty: atributy</span><span class="sxs-lookup"><span data-stu-id="66588-347">\<xs:restriction> for enumerations: attributes</span></span>

|<span data-ttu-id="66588-348">Atribut</span><span class="sxs-lookup"><span data-stu-id="66588-348">Attribute</span></span>|<span data-ttu-id="66588-349">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-349">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="66588-350">Pokud je přítomen, musí být `xs:string` .</span><span class="sxs-lookup"><span data-stu-id="66588-350">If present, must be `xs:string`.</span></span>|
|`id`|<span data-ttu-id="66588-351">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-351">Ignored.</span></span>|

### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="66588-352">\<xs:restriction>pro výčty: obsah</span><span class="sxs-lookup"><span data-stu-id="66588-352">\<xs:restriction> for enumerations: contents</span></span>

|<span data-ttu-id="66588-353">Obsah</span><span class="sxs-lookup"><span data-stu-id="66588-353">Contents</span></span>|<span data-ttu-id="66588-354">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-354">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="66588-355">Je-li k dispozici, musí se jednat o omezení výčtu podporované kontraktem dat (v této části).</span><span class="sxs-lookup"><span data-stu-id="66588-355">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|
|`minExclusive`|<span data-ttu-id="66588-356">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-356">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="66588-357">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-357">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="66588-358">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-358">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="66588-359">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-359">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="66588-360">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-360">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="66588-361">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-361">Ignored.</span></span>|
|`length`|<span data-ttu-id="66588-362">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-362">Forbidden.</span></span>|
|`minLength`|<span data-ttu-id="66588-363">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-363">Forbidden.</span></span>|
|`maxLength`|<span data-ttu-id="66588-364">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-364">Forbidden.</span></span>|
|`enumeration`|<span data-ttu-id="66588-365">Podporuje se.</span><span class="sxs-lookup"><span data-stu-id="66588-365">Supported.</span></span> <span data-ttu-id="66588-366">Výčet "ID" se ignoruje a hodnota "value" se mapuje na název hodnoty ve kontraktu dat výčtu.</span><span class="sxs-lookup"><span data-stu-id="66588-366">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|
|`whiteSpace`|<span data-ttu-id="66588-367">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-367">Forbidden.</span></span>|
|`pattern`|<span data-ttu-id="66588-368">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-368">Forbidden.</span></span>|
|<span data-ttu-id="66588-369">obsahovat</span><span class="sxs-lookup"><span data-stu-id="66588-369">(empty)</span></span>|<span data-ttu-id="66588-370">Podporováno, mapuje se na prázdný typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="66588-370">Supported, maps to empty enumeration type.</span></span>|

 <span data-ttu-id="66588-371">Následující kód ukazuje třídu výčtu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="66588-371">The following code shows a C# enumeration class.</span></span>

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

<span data-ttu-id="66588-372">Tato třída je mapována na následující schéma pomocí `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="66588-372">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="66588-373">Pokud hodnoty výčtu začínají na 1, `xs:annotation` bloky se nevygenerují.</span><span class="sxs-lookup"><span data-stu-id="66588-373">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>

```xml
<xs:simpleType name="MyEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="first">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          3
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
    <xs:enumeration value="second">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          4
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
  </xs:restriction>
</xs:simpleType>
```

### \<xs:list>

<span data-ttu-id="66588-374">`DataContractSerializer`mapuje výčtové typy označené `System.FlagsAttribute` s `xs:list` odvozeným z `xs:string` .</span><span class="sxs-lookup"><span data-stu-id="66588-374">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="66588-375">Žádné jiné `xs:list` varianty nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="66588-375">No other `xs:list` variations are supported.</span></span>

### <a name="xslist-attributes"></a><span data-ttu-id="66588-376">\<xs:list>: atributy</span><span class="sxs-lookup"><span data-stu-id="66588-376">\<xs:list>: attributes</span></span>

|<span data-ttu-id="66588-377">Atribut</span><span class="sxs-lookup"><span data-stu-id="66588-377">Attribute</span></span>|<span data-ttu-id="66588-378">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-378">Schema</span></span>|
|---------------|------------|
|`itemType`|<span data-ttu-id="66588-379">Zakázán.</span><span class="sxs-lookup"><span data-stu-id="66588-379">Forbidden.</span></span>|
|`id`|<span data-ttu-id="66588-380">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-380">Ignored.</span></span>|

### <a name="xslist-contents"></a><span data-ttu-id="66588-381">\<xs:list>: obsah</span><span class="sxs-lookup"><span data-stu-id="66588-381">\<xs:list>: contents</span></span>

|<span data-ttu-id="66588-382">Obsah</span><span class="sxs-lookup"><span data-stu-id="66588-382">Contents</span></span>|<span data-ttu-id="66588-383">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-383">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="66588-384">Musí být omezením `xs:string` použití `xs:enumeration` omezující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="66588-384">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|

<span data-ttu-id="66588-385">Pokud hodnota výčtu nedodržuje mocninu 2 (výchozí pro příznaky), hodnota je uložena v `xs:annotation/xs:appInfo/ser:EnumerationValue` elementu.</span><span class="sxs-lookup"><span data-stu-id="66588-385">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>

<span data-ttu-id="66588-386">Například následující kód označuje typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="66588-386">For example, the following code flags an enumeration type.</span></span>

```csharp
[Flags]
public enum AuthFlags
{
  AuthAnonymous = 1,
  AuthBasic = 2,
  AuthNTLM = 4,
  AuthMD5 = 16,
  AuthWindowsLiveID = 64,
}
```

<span data-ttu-id="66588-387">Tento typ se mapuje k následujícímu schématu.</span><span class="sxs-lookup"><span data-stu-id="66588-387">This type maps to the following schema.</span></span>

```xml
<xs:simpleType name="AuthFlags">
    <xs:list>
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="AuthAnonymous" />
          <xs:enumeration value="AuthBasic" />
          <xs:enumeration value="AuthNTLM" />
          <xs:enumeration value="AuthMD5">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
          <xs:enumeration value="AuthWindowsLiveID">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
        </xs:restriction>
      </xs:simpleType>
    </xs:list>
  </xs:simpleType>
```

## <a name="inheritance"></a><span data-ttu-id="66588-388">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="66588-388">Inheritance</span></span>

### <a name="general-rules"></a><span data-ttu-id="66588-389">Obecná pravidla</span><span class="sxs-lookup"><span data-stu-id="66588-389">General rules</span></span>

<span data-ttu-id="66588-390">Kontrakt dat může dědit od jiného kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="66588-390">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="66588-391">Tyto kontrakty dat jsou mapovány na základ a jsou odvozeny pomocí typů rozšíření pomocí `<xs:extension>` konstrukce schématu XML.</span><span class="sxs-lookup"><span data-stu-id="66588-391">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>

<span data-ttu-id="66588-392">Kontrakt dat nemůže dědit od kontraktu dat kolekce.</span><span class="sxs-lookup"><span data-stu-id="66588-392">A data contract cannot inherit from a collection data contract.</span></span>

<span data-ttu-id="66588-393">Například následující kód je kontraktem dat.</span><span class="sxs-lookup"><span data-stu-id="66588-393">For example, the following code is a data contract.</span></span>

```csharp
[DataContract]
public class Person
{
  [DataMember]
  public string Name;
}
[DataContract]
public class Employee : Person
{
  [DataMember]
  public int ID;
}
```

<span data-ttu-id="66588-394">Tato kontrakt dat se mapuje na následující deklaraci typu schématu XML.</span><span class="sxs-lookup"><span data-stu-id="66588-394">This data contract maps to the following XML Schema type declaration.</span></span>

```xml
<xs:complexType name="Employee">
 <xs:complexContent mixed="false">
  <xs:extension base="tns:Person">
   <xs:sequence>
    <xs:element minOccurs="0" name="ID" type="xs:int"/>
   </xs:sequence>
  </xs:extension>
 </xs:complexContent>
</xs:complexType>
<xs:complexType name="Person">
 <xs:sequence>
  <xs:element minOccurs="0" name="Name"
    nillable="true" type="xs:string"/>
 </xs:sequence>
</xs:complexType>
```

### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="66588-395">\<xs:complexContent>: atributy</span><span class="sxs-lookup"><span data-stu-id="66588-395">\<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="66588-396">Atribut</span><span class="sxs-lookup"><span data-stu-id="66588-396">Attribute</span></span>|<span data-ttu-id="66588-397">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-397">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="66588-398">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-398">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="66588-399">Hodnota musí být false.</span><span class="sxs-lookup"><span data-stu-id="66588-399">Must be false.</span></span>|

### <a name="xscomplexcontent-contents"></a><span data-ttu-id="66588-400">\<xs:complexContent>: obsah</span><span class="sxs-lookup"><span data-stu-id="66588-400">\<xs:complexContent>: contents</span></span>

|<span data-ttu-id="66588-401">Obsah</span><span class="sxs-lookup"><span data-stu-id="66588-401">Contents</span></span>|<span data-ttu-id="66588-402">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-402">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="66588-403">Zakázáno, s výjimkou případů, kdy je Base = " `xs:anyType` ".</span><span class="sxs-lookup"><span data-stu-id="66588-403">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="66588-404">Druhý je ekvivalentní umístění obsahu `xs:restriction` přímo pod kontejnerem `xs:complexContent` .</span><span class="sxs-lookup"><span data-stu-id="66588-404">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|
|`extension`|<span data-ttu-id="66588-405">Podporuje se.</span><span class="sxs-lookup"><span data-stu-id="66588-405">Supported.</span></span> <span data-ttu-id="66588-406">Provede mapování na dědičnost kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="66588-406">Maps to data contract inheritance.</span></span>|

### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="66588-407">\<xs:extension>v \<xs:complexContent> : atributy</span><span class="sxs-lookup"><span data-stu-id="66588-407">\<xs:extension> in \<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="66588-408">Atribut</span><span class="sxs-lookup"><span data-stu-id="66588-408">Attribute</span></span>|<span data-ttu-id="66588-409">Schéma</span><span class="sxs-lookup"><span data-stu-id="66588-409">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="66588-410">Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="66588-410">Ignored.</span></span>|
|`base`|<span data-ttu-id="66588-411">Podporuje se.</span><span class="sxs-lookup"><span data-stu-id="66588-411">Supported.</span></span> <span data-ttu-id="66588-412">Provede mapování základního typu kontraktu dat, z něhož tento typ dědí.</span><span class="sxs-lookup"><span data-stu-id="66588-412">Maps to the base data contract type that this type inherits from.</span></span>|

### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="66588-413">\<xs:extension>v \<xs:complexContent> : obsah</span><span class="sxs-lookup"><span data-stu-id="66588-413">\<xs:extension> in \<xs:complexContent>: contents</span></span>

<span data-ttu-id="66588-414">Pravidla jsou stejná jako u `<xs:complexType>` obsahu.</span><span class="sxs-lookup"><span data-stu-id="66588-414">The rules are the same as for `<xs:complexType>` contents.</span></span>

<span data-ttu-id="66588-415">Pokud `<xs:sequence>` je k dispozici, jeho členské prvky budou mapovány na další datové členy, které jsou přítomny v odvozeném kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="66588-415">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>

<span data-ttu-id="66588-416">Pokud odvozený typ obsahuje element se stejným názvem jako element v základním typu, je deklarace duplicitních prvků mapována na datový člen s názvem, který je vygenerován jako jedinečný.</span><span class="sxs-lookup"><span data-stu-id="66588-416">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="66588-417">Kladné celočíselná čísla jsou přidána do názvu datového členu ("Člen1", "member2" atd.), dokud nebude nalezen jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="66588-417">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="66588-418">Naopak</span><span class="sxs-lookup"><span data-stu-id="66588-418">Conversely:</span></span>

- <span data-ttu-id="66588-419">Pokud má odvozená kontrakt dat datový člen se stejným názvem a typem jako datový člen v základní kontraktu dat, `DataContractSerializer` vygeneruje tento odpovídající prvek v odvozeném typu.</span><span class="sxs-lookup"><span data-stu-id="66588-419">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>

- <span data-ttu-id="66588-420">Pokud má odvozená kontrakt dat datový člen se stejným názvem jako datový člen v základní kontraktu dat, ale jiný typ, `DataContractSerializer` importuje schéma s prvkem typu `xs:anyType` v obou základních typech i v deklaracích odvozených typů.</span><span class="sxs-lookup"><span data-stu-id="66588-420">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="66588-421">Původní název typu se zachová v `xs:annotations/xs:appInfo/ser:ActualType/@Name` .</span><span class="sxs-lookup"><span data-stu-id="66588-421">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>

<span data-ttu-id="66588-422">Obě varianty mohou vést ke schématu s nejednoznačným obsahem modelu, který závisí na pořadí příslušných datových členů.</span><span class="sxs-lookup"><span data-stu-id="66588-422">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>

## <a name="typeprimitive-mapping"></a><span data-ttu-id="66588-423">Mapování typů a primitivních hodnot</span><span class="sxs-lookup"><span data-stu-id="66588-423">Type/primitive mapping</span></span>

<span data-ttu-id="66588-424">`DataContractSerializer`Používá následující mapování pro primitivní typy schémat XML.</span><span class="sxs-lookup"><span data-stu-id="66588-424">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>

|<span data-ttu-id="66588-425">Typ XSD</span><span class="sxs-lookup"><span data-stu-id="66588-425">XSD type</span></span>|<span data-ttu-id="66588-426">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="66588-426">.NET type</span></span>|
|--------------|---------------|
|`anyType`|<span data-ttu-id="66588-427"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="66588-427"><xref:System.Object>.</span></span>|
|`anySimpleType`|<span data-ttu-id="66588-428"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-428"><xref:System.String>.</span></span>|
|`duration`|<span data-ttu-id="66588-429"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="66588-429"><xref:System.TimeSpan>.</span></span>|
|`dateTime`|<span data-ttu-id="66588-430"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="66588-430"><xref:System.DateTime>.</span></span>|
|`dateTimeOffset`|<span data-ttu-id="66588-431"><xref:System.DateTime>a <xref:System.TimeSpan> pro posun.</span><span class="sxs-lookup"><span data-stu-id="66588-431"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="66588-432">Viz serializace DateTimeOffset níže.</span><span class="sxs-lookup"><span data-stu-id="66588-432">See DateTimeOffset Serialization below.</span></span>|
|`time`|<span data-ttu-id="66588-433"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-433"><xref:System.String>.</span></span>|
|`date`|<span data-ttu-id="66588-434"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-434"><xref:System.String>.</span></span>|
|`gYearMonth`|<span data-ttu-id="66588-435"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-435"><xref:System.String>.</span></span>|
|`gYear`|<span data-ttu-id="66588-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-436"><xref:System.String>.</span></span>|
|`gMonthDay`|<span data-ttu-id="66588-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-437"><xref:System.String>.</span></span>|
|`gDay`|<span data-ttu-id="66588-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-438"><xref:System.String>.</span></span>|
|`gMonth`|<span data-ttu-id="66588-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-439"><xref:System.String>.</span></span>|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<span data-ttu-id="66588-440"><xref:System.Byte>skupin.</span><span class="sxs-lookup"><span data-stu-id="66588-440"><xref:System.Byte> array.</span></span>|
|`hexBinary`|<span data-ttu-id="66588-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-441"><xref:System.String>.</span></span>|
|`float`|<span data-ttu-id="66588-442"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="66588-442"><xref:System.Single>.</span></span>|
|`double`|<span data-ttu-id="66588-443"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="66588-443"><xref:System.Double>.</span></span>|
|`anyURI`|<span data-ttu-id="66588-444"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="66588-444"><xref:System.Uri>.</span></span>|
|`QName`|<span data-ttu-id="66588-445"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="66588-445"><xref:System.Xml.XmlQualifiedName>.</span></span>|
|`string`|<span data-ttu-id="66588-446"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-446"><xref:System.String>.</span></span>|
|`normalizedString`|<span data-ttu-id="66588-447"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-447"><xref:System.String>.</span></span>|
|`token`|<span data-ttu-id="66588-448"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-448"><xref:System.String>.</span></span>|
|`language`|<span data-ttu-id="66588-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-449"><xref:System.String>.</span></span>|
|`Name`|<span data-ttu-id="66588-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-450"><xref:System.String>.</span></span>|
|`NCName`|<span data-ttu-id="66588-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-451"><xref:System.String>.</span></span>|
|`ID`|<span data-ttu-id="66588-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-452"><xref:System.String>.</span></span>|
|`IDREF`|<span data-ttu-id="66588-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-453"><xref:System.String>.</span></span>|
|`IDREFS`|<span data-ttu-id="66588-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-454"><xref:System.String>.</span></span>|
|`ENTITY`|<span data-ttu-id="66588-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-455"><xref:System.String>.</span></span>|
|`ENTITIES`|<span data-ttu-id="66588-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-456"><xref:System.String>.</span></span>|
|`NMTOKEN`|<span data-ttu-id="66588-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-457"><xref:System.String>.</span></span>|
|`NMTOKENS`|<span data-ttu-id="66588-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="66588-458"><xref:System.String>.</span></span>|
|`decimal`|<span data-ttu-id="66588-459"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="66588-459"><xref:System.Decimal>.</span></span>|
|`integer`|<span data-ttu-id="66588-460"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="66588-460"><xref:System.Int64>.</span></span>|
|`nonPositiveInteger`|<span data-ttu-id="66588-461"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="66588-461"><xref:System.Int64>.</span></span>|
|`negativeInteger`|<span data-ttu-id="66588-462"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="66588-462"><xref:System.Int64>.</span></span>|
|`long`|<span data-ttu-id="66588-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="66588-463"><xref:System.Int64>.</span></span>|
|`int`|<span data-ttu-id="66588-464"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="66588-464"><xref:System.Int32>.</span></span>|
|`short`|<span data-ttu-id="66588-465"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="66588-465"><xref:System.Int16>.</span></span>|
|`Byte`|<span data-ttu-id="66588-466"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="66588-466"><xref:System.SByte>.</span></span>|
|`nonNegativeInteger`|<span data-ttu-id="66588-467"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="66588-467"><xref:System.Int64>.</span></span>|
|`unsignedLong`|<span data-ttu-id="66588-468"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="66588-468"><xref:System.UInt64>.</span></span>|
|`unsignedInt`|<span data-ttu-id="66588-469"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="66588-469"><xref:System.UInt32>.</span></span>|
|`unsignedShort`|<span data-ttu-id="66588-470"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="66588-470"><xref:System.UInt16>.</span></span>|
|`unsignedByte`|<span data-ttu-id="66588-471"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="66588-471"><xref:System.Byte>.</span></span>|
|`positiveInteger`|<span data-ttu-id="66588-472"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="66588-472"><xref:System.Int64>.</span></span>|

## <a name="iserializable-types-mapping"></a><span data-ttu-id="66588-473">Mapování typů ISerializable</span><span class="sxs-lookup"><span data-stu-id="66588-473">ISerializable types mapping</span></span>

<span data-ttu-id="66588-474">V .NET Framework verze 1,0 <xref:System.Runtime.Serialization.ISerializable> byla představena jako obecný mechanismus pro serializaci objektů pro trvalost nebo přenos dat.</span><span class="sxs-lookup"><span data-stu-id="66588-474">In .NET Framework version 1.0, <xref:System.Runtime.Serialization.ISerializable> was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="66588-475">Existuje mnoho typů .NET Framework, které implementují `ISerializable` a které je možné předat mezi aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="66588-475">There are many .NET Framework types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="66588-476"><xref:System.Runtime.Serialization.DataContractSerializer>přirozeně poskytuje podporu pro `ISerializable` třídy.</span><span class="sxs-lookup"><span data-stu-id="66588-476"><xref:System.Runtime.Serialization.DataContractSerializer> naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="66588-477">`DataContractSerializer`Mapy `ISerializable` implementují typy schématu, které se liší pouze názvem QName (kvalifikovaný název) typu a jsou účinné kolekce vlastností.</span><span class="sxs-lookup"><span data-stu-id="66588-477">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="66588-478">Například `DataContractSerializer` mapuje <xref:System.Exception> na následující typ XSD v `http://schemas.datacontract.org/2004/07/System` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="66588-478">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

<span data-ttu-id="66588-479">Volitelný atribut `ser:FactoryType` deklarovaný ve schématu serializace kontraktu dat odkazuje na třídu factory, která může deserializovat typ.</span><span class="sxs-lookup"><span data-stu-id="66588-479">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="66588-480">Třída factory musí být součástí kolekce známých typů `DataContractSerializer` používané instance.</span><span class="sxs-lookup"><span data-stu-id="66588-480">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="66588-481">Další informace o známých typech najdete v tématu [známé typy kontraktu dat](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="66588-481">For more information about known types, see [Data Contract Known Types](data-contract-known-types.md).</span></span>

## <a name="datacontract-serialization-schema"></a><span data-ttu-id="66588-482">Schéma serializace DataContract</span><span class="sxs-lookup"><span data-stu-id="66588-482">DataContract Serialization Schema</span></span>

<span data-ttu-id="66588-483">Několik schémat vyexportovaných `DataContractSerializer` typy použití, prvky a atributy z speciálního oboru názvů serializace kontraktu dat:</span><span class="sxs-lookup"><span data-stu-id="66588-483">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>

`http://schemas.microsoft.com/2003/10/Serialization`

<span data-ttu-id="66588-484">Následuje kompletní deklarace schématu serializace kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="66588-484">The following is a complete Data Contract Serialization schema declaration.</span></span>

```xml
<xs:schema attributeFormDefault="qualified"
   elementFormDefault="qualified"
   targetNamespace =
    "http://schemas.microsoft.com/2003/10/Serialization/"
   xmlns:xs="http://www.w3.org/2001/XMLSchema"
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">

 <!-- Top-level elements for primitive types. -->
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>
 <xs:element name="base64Binary"
       nillable="true" type="xs:base64Binary"/>
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>
 <xs:element name="byte" nillable="true" type="xs:byte"/>
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>
 <xs:element name="double" nillable="true" type="xs:double"/>
 <xs:element name="float" nillable="true" type="xs:float"/>
 <xs:element name="int" nillable="true" type="xs:int"/>
 <xs:element name="long" nillable="true" type="xs:long"/>
 <xs:element name="QName" nillable="true" type="xs:QName"/>
 <xs:element name="short" nillable="true" type="xs:short"/>
 <xs:element name="string" nillable="true" type="xs:string"/>
 <xs:element name="unsignedByte"
       nillable="true" type="xs:unsignedByte"/>
 <xs:element name="unsignedInt"
       nillable="true" type="xs:unsignedInt"/>
 <xs:element name="unsignedLong"
       nillable="true" type="xs:unsignedLong"/>
 <xs:element name="unsignedShort"
       nillable="true" type="xs:unsignedShort"/>

 <!-- Primitive types introduced for certain .NET simple types. -->
 <xs:element name="char" nillable="true" type="tns:char"/>
 <xs:simpleType name="char">
  <xs:restriction base="xs:int"/>
 </xs:simpleType>

 <!-- xs:duration is restricted to an ordered value space,
    to map to System.TimeSpan -->
 <xs:element name="duration" nillable="true" type="tns:duration"/>
 <xs:simpleType name="duration">
  <xs:restriction base="xs:duration">
   <xs:pattern
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>
  </xs:restriction>
 </xs:simpleType>

 <xs:element name="guid" nillable="true" type="tns:guid"/>
 <xs:simpleType name="guid">
  <xs:restriction base="xs:string">
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>
  </xs:restriction>
 </xs:simpleType>

 <!-- This is used for schemas exported from ISerializable type. -->
 <xs:attribute name="FactoryType" type="xs:QName"/>
</xs:schema>
```

<span data-ttu-id="66588-485">Měli byste si uvědomit následující:</span><span class="sxs-lookup"><span data-stu-id="66588-485">The following should be noted:</span></span>

- <span data-ttu-id="66588-486">`ser:char`je představena pro reprezentaci znaků Unicode typu <xref:System.Char> .</span><span class="sxs-lookup"><span data-stu-id="66588-486">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>

- <span data-ttu-id="66588-487">`valuespace`Z `xs:duration` je snížen na seřazenou sadu, aby mohla být namapována na <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="66588-487">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>

- <span data-ttu-id="66588-488">`FactoryType`se používá v schématech exportovaných z typů, které jsou odvozeny z <xref:System.Runtime.Serialization.ISerializable> .</span><span class="sxs-lookup"><span data-stu-id="66588-488">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>

## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="66588-489">Import schémat jiných než DataContract</span><span class="sxs-lookup"><span data-stu-id="66588-489">Importing non-DataContract schemas</span></span>

<span data-ttu-id="66588-490">`DataContractSerializer`má `ImportXmlTypes` možnost Povolit import schémat, která neodpovídají `DataContractSerializer` profilu XSD (viz <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> vlastnost).</span><span class="sxs-lookup"><span data-stu-id="66588-490">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="66588-491">Nastavením této možnosti `true` umožníte přijetí nevyhovujících typů schémat a jejich mapování na následující implementaci a <xref:System.Xml.Serialization.IXmlSerializable> zabalení pole <xref:System.Xml.XmlNode> (pouze název třídy se liší).</span><span class="sxs-lookup"><span data-stu-id="66588-491">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>

```csharp
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]
public partial class Person : object, IXmlSerializable
{
  private XmlNode[] nodesField;
  private static XmlQualifiedName typeName =
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");
  public XmlNode[] Nodes
  {
    get {return this.nodesField;}
    set {this.nodesField = value;}
  }
  public void ReadXml(XmlReader reader)
  {
    this.nodesField = XmlSerializableServices.ReadNodes(reader);
  }
  public void WriteXml(XmlWriter writer)
  {
    XmlSerializableServices.WriteNodes(writer, this.Nodes);
  }
  public System.Xml.Schema.XmlSchema GetSchema()
  {
    return null;
  }
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)
  {
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);
    return typeName;
  }
}
```

## <a name="datetimeoffset-serialization"></a><span data-ttu-id="66588-492">Serializace DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="66588-492">DateTimeOffset Serialization</span></span>

<span data-ttu-id="66588-493">Není <xref:System.DateTimeOffset> považována za primitivní typ.</span><span class="sxs-lookup"><span data-stu-id="66588-493">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="66588-494">Místo toho je serializován jako složitý prvek se dvěma částmi.</span><span class="sxs-lookup"><span data-stu-id="66588-494">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="66588-495">První část představuje datum a druhá část představuje posun od data a času.</span><span class="sxs-lookup"><span data-stu-id="66588-495">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="66588-496">Příklad serializované hodnoty DateTimeOffset je zobrazen v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="66588-496">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>

```xml
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">
  <DateTime i:type="b:dateTime" xmlns=""
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00
  </DateTime>
  <OffsetMinutes i:type="b:short" xmlns=""
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480
   </OffsetMinutes>
</OffSet>
```

<span data-ttu-id="66588-497">Schéma je následující.</span><span class="sxs-lookup"><span data-stu-id="66588-497">The schema is as follows.</span></span>

```xml
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">
   <xs:complexType name="DateTimeOffset">
      <xs:sequence minOccurs="1" maxOccurs="1">
         <xs:element name="DateTime" type="xs:dateTime"
         minOccurs="1" maxOccurs="1" />
         <xs:element name="OffsetMinutes" type="xs:short"
         minOccurs="1" maxOccurs="1" />
      </xs:sequence>
   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a><span data-ttu-id="66588-498">Viz také</span><span class="sxs-lookup"><span data-stu-id="66588-498">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [<span data-ttu-id="66588-499">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="66588-499">Using Data Contracts</span></span>](using-data-contracts.md)
