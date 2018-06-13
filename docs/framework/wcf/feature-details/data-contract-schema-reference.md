---
title: Schéma kontraktů dat – referenční informace
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: 06bc79e059300d448ababa87974b590f54f7984c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496796"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="bf101-102">Schéma kontraktů dat – referenční informace</span><span class="sxs-lookup"><span data-stu-id="bf101-102">Data Contract Schema Reference</span></span>
<span data-ttu-id="bf101-103">Toto téma popisuje některé z schéma XML (XSD) používané <xref:System.Runtime.Serialization.DataContractSerializer> k popisu common language runtime (CLR) typy pro serializaci XML.</span><span class="sxs-lookup"><span data-stu-id="bf101-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>  
  
## <a name="datacontractserializer-mappings"></a><span data-ttu-id="bf101-104">Mapování DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="bf101-104">DataContractSerializer Mappings</span></span>  
 <span data-ttu-id="bf101-105">`DataContractSerializer` Mapuje typy CLR XSD při exportu metadat ze služby Windows Communication Foundation (WCF) pomocí koncový bod metadat nebo [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bf101-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="bf101-106">Další informace najdete v tématu [serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="bf101-106">For more information, see [Data Contract Serializer](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span></span>  
  
 <span data-ttu-id="bf101-107">`DataContractSerializer` Také mapuje XSD typy CLR při Svcutil.exe se používá pro přístup k webové služby popis Language (WSDL) nebo XSD dokumentů a generovat kontrakty dat pro služby nebo klientů.</span><span class="sxs-lookup"><span data-stu-id="bf101-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>  
  
 <span data-ttu-id="bf101-108">Pouze instance schématu XML, které v souladu s požadavky uvedené v tomto dokumentu lze mapovat na typy CLR pomocí `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="bf101-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>  
  
### <a name="support-levels"></a><span data-ttu-id="bf101-109">Úrovně podpory</span><span class="sxs-lookup"><span data-stu-id="bf101-109">Support Levels</span></span>  
 <span data-ttu-id="bf101-110">`DataContractSerializer` Poskytuje následující úrovně podpory pro danou funkci schématu XML:</span><span class="sxs-lookup"><span data-stu-id="bf101-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>  
  
-   <span data-ttu-id="bf101-111">**Podporované**.</span><span class="sxs-lookup"><span data-stu-id="bf101-111">**Supported**.</span></span> <span data-ttu-id="bf101-112">Je explicitní mapování z této funkce se CLR typy atributů (nebo obě) pomocí `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="bf101-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>  
  
-   <span data-ttu-id="bf101-113">**Ignorovat**.</span><span class="sxs-lookup"><span data-stu-id="bf101-113">**Ignored**.</span></span> <span data-ttu-id="bf101-114">Tato funkce je povolena v schémata importovat pomocí `DataContractSerializer`, ale nemá žádný vliv na generování kódu.</span><span class="sxs-lookup"><span data-stu-id="bf101-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>  
  
-   <span data-ttu-id="bf101-115">**Je zakázané**.</span><span class="sxs-lookup"><span data-stu-id="bf101-115">**Forbidden**.</span></span> <span data-ttu-id="bf101-116">`DataContractSerializer` Nepodporuje import schématu pomocí funkce.</span><span class="sxs-lookup"><span data-stu-id="bf101-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="bf101-117">Například Svcutil.exe při přístupu k WSDL se schématem, které používá funkci, se vrátí k používání <xref:System.Xml.Serialization.XmlSerializer> místo.</span><span class="sxs-lookup"><span data-stu-id="bf101-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="bf101-118">Toto je ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="bf101-118">This is by default.</span></span>  
  
## <a name="general-information"></a><span data-ttu-id="bf101-119">Obecné informace</span><span class="sxs-lookup"><span data-stu-id="bf101-119">General Information</span></span>  
  
-   <span data-ttu-id="bf101-120">Obor názvů schématu je popsána v [schématu XML](http://go.microsoft.com/fwlink/?LinkId=95475).</span><span class="sxs-lookup"><span data-stu-id="bf101-120">The schema namespace is described at [XML Schema](http://go.microsoft.com/fwlink/?LinkId=95475).</span></span> <span data-ttu-id="bf101-121">V tomto dokumentu se používá předpona "xs".</span><span class="sxs-lookup"><span data-stu-id="bf101-121">The prefix "xs" is used in this document.</span></span>  
  
-   <span data-ttu-id="bf101-122">Žádné atributy k oboru názvů na schéma se ignorují.</span><span class="sxs-lookup"><span data-stu-id="bf101-122">Any attributes with a non-schema namespace are ignored.</span></span>  
  
-   <span data-ttu-id="bf101-123">Žádné poznámky (s výjimkou těch popsaných v tomto dokumentu) se ignorují.</span><span class="sxs-lookup"><span data-stu-id="bf101-123">Any annotations (except for those described in this document) are ignored.</span></span>  
  
### <a name="xsschema-attributes"></a><span data-ttu-id="bf101-124">\<xs:Schema >: atributy</span><span class="sxs-lookup"><span data-stu-id="bf101-124">\<xs:schema>: attributes</span></span>  
  
|<span data-ttu-id="bf101-125">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf101-125">Attribute</span></span>|<span data-ttu-id="bf101-126">Kontraktu</span><span class="sxs-lookup"><span data-stu-id="bf101-126">DataContract</span></span>|  
|---------------|------------------|  
|`attributeFormDefault`|<span data-ttu-id="bf101-127">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-127">Ignored.</span></span>|  
|`blockDefault`|<span data-ttu-id="bf101-128">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-128">Ignored.</span></span>|  
|`elementFormDefault`|<span data-ttu-id="bf101-129">Musí být kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="bf101-129">Must be qualified.</span></span> <span data-ttu-id="bf101-130">Všechny elementy musí být kvalifikovaný pro schématu jsou podporováni `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="bf101-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="bf101-131">To můžete udělat buď nastavení xs:schema/@elementFormDefault "kvalifikovaný" nebo nastavením xs:element/@form na "kvalifikovaný" na každý jednotlivý prvek deklarace.</span><span class="sxs-lookup"><span data-stu-id="bf101-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|  
|`finalDefault`|<span data-ttu-id="bf101-132">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-132">Ignored.</span></span>|  
|`Id`|<span data-ttu-id="bf101-133">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-133">Ignored.</span></span>|  
|`targetNamespace`|<span data-ttu-id="bf101-134">Podporované a mapované na obor názvů kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="bf101-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="bf101-135">Pokud tento atribut nezadá, použije se prázdný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="bf101-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="bf101-136">Nemůže být vyhrazený obor názvů http://schemas.microsoft.com/2003/10/Serialization/.</span><span class="sxs-lookup"><span data-stu-id="bf101-136">Cannot be the reserved namespace http://schemas.microsoft.com/2003/10/Serialization/.</span></span>|  
|`version`|<span data-ttu-id="bf101-137">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-137">Ignored.</span></span>|  
  
### <a name="xsschema-contents"></a><span data-ttu-id="bf101-138">\<xs:Schema >: obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-138">\<xs:schema>: contents</span></span>  
  
|<span data-ttu-id="bf101-139">Obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-139">Contents</span></span>|<span data-ttu-id="bf101-140">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-140">Schema</span></span>|  
|--------------|------------|  
|`include`|<span data-ttu-id="bf101-141">Podporováno.</span><span class="sxs-lookup"><span data-stu-id="bf101-141">Supported.</span></span> <span data-ttu-id="bf101-142">`DataContractSerializer` podporuje xs: zahrnout a xs:import.</span><span class="sxs-lookup"><span data-stu-id="bf101-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="bf101-143">Ale Svcutil.exe omezuje následující `xs:include/@schemaLocation` a `xs:import/@location` odkazuje při načítání metadat z místního souboru.</span><span class="sxs-lookup"><span data-stu-id="bf101-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="bf101-144">Seznam souborů schématu musí být předán přes mechanismus out-of-band a ne prostřednictvím `include` v tomto případě; `include`d schématu dokumenty jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="bf101-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`redefine`|<span data-ttu-id="bf101-145">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-145">Forbidden.</span></span> <span data-ttu-id="bf101-146">Použití `xs:redefine` je zakázána `DataContractSerializer` z bezpečnostních důvodů: `x:redefine` vyžaduje `schemaLocation` -li být zahájen.</span><span class="sxs-lookup"><span data-stu-id="bf101-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="bf101-147">V některých případech Svcutil.exe pomocí kontraktu omezuje použití `schemaLocation`.</span><span class="sxs-lookup"><span data-stu-id="bf101-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|  
|`import`|<span data-ttu-id="bf101-148">Podporováno.</span><span class="sxs-lookup"><span data-stu-id="bf101-148">Supported.</span></span> <span data-ttu-id="bf101-149">`DataContractSerializer` podporuje `xs:include` a `xs:import`.</span><span class="sxs-lookup"><span data-stu-id="bf101-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="bf101-150">Ale Svcutil.exe omezuje následující `xs:include/@schemaLocation` a `xs:import/@location` odkazuje při načítání metadat z místního souboru.</span><span class="sxs-lookup"><span data-stu-id="bf101-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="bf101-151">Seznam souborů schématu musí být předán přes mechanismus out-of-band a ne prostřednictvím `include` v tomto případě; `include`d schématu dokumenty jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="bf101-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`simpleType`|<span data-ttu-id="bf101-152">Podporováno.</span><span class="sxs-lookup"><span data-stu-id="bf101-152">Supported.</span></span> <span data-ttu-id="bf101-153">Najdete v článku `xs:simpleType` oddílu.</span><span class="sxs-lookup"><span data-stu-id="bf101-153">See the `xs:simpleType` section.</span></span>|  
|`complexType`|<span data-ttu-id="bf101-154">Nepodporuje mapuje kontrakty dat.</span><span class="sxs-lookup"><span data-stu-id="bf101-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="bf101-155">Najdete v článku `xs:complexType` oddílu.</span><span class="sxs-lookup"><span data-stu-id="bf101-155">See the `xs:complexType` section.</span></span>|  
|`group`|<span data-ttu-id="bf101-156">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-156">Ignored.</span></span> <span data-ttu-id="bf101-157">`DataContractSerializer` nepodporuje použití `xs:group`, `xs:attributeGroup`, a `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="bf101-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="bf101-158">Tyto deklarace jsou ignorovány jako podřízené objekty `xs:schema`, ale nelze na něj odkazovat z uvnitř `complexType` nebo jiné podporované konstrukce.</span><span class="sxs-lookup"><span data-stu-id="bf101-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`attributeGroup`|<span data-ttu-id="bf101-159">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-159">Ignored.</span></span> <span data-ttu-id="bf101-160">`DataContractSerializer` nepodporuje použití `xs:group`, `xs:attributeGroup`, a `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="bf101-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="bf101-161">Tyto deklarace jsou ignorovány jako podřízené objekty `xs:schema`, ale nelze na něj odkazovat z uvnitř `complexType` nebo jiné podporované konstrukce.</span><span class="sxs-lookup"><span data-stu-id="bf101-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`element`|<span data-ttu-id="bf101-162">Podporováno.</span><span class="sxs-lookup"><span data-stu-id="bf101-162">Supported.</span></span> <span data-ttu-id="bf101-163">Najdete v části globální Element deklarace (NĚNÁ).</span><span class="sxs-lookup"><span data-stu-id="bf101-163">See Global Element Declaration (GED).</span></span>|  
|`attribute`|<span data-ttu-id="bf101-164">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-164">Ignored.</span></span> <span data-ttu-id="bf101-165">`DataContractSerializer` nepodporuje použití `xs:group`, `xs:attributeGroup`, a `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="bf101-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="bf101-166">Tyto deklarace jsou ignorovány jako podřízené objekty `xs:schema`, ale nelze na něj odkazovat z uvnitř `complexType` nebo jiné podporované konstrukce.</span><span class="sxs-lookup"><span data-stu-id="bf101-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`notation`|<span data-ttu-id="bf101-167">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-167">Ignored.</span></span>|  
  
## <a name="complex-types--xscomplextype"></a><span data-ttu-id="bf101-168">Komplexní typy – \<xs:complexType ></span><span class="sxs-lookup"><span data-stu-id="bf101-168">Complex Types – \<xs:complexType></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="bf101-169">Obecné informace</span><span class="sxs-lookup"><span data-stu-id="bf101-169">General Information</span></span>  
 <span data-ttu-id="bf101-170">Každý komplexní typ \<xs:complexType > mapuje kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="bf101-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>  
  
### <a name="xscomplextype-attributes"></a><span data-ttu-id="bf101-171">\<xs:complexType >: atributy</span><span class="sxs-lookup"><span data-stu-id="bf101-171">\<xs:complexType>: attributes</span></span>  
  
|<span data-ttu-id="bf101-172">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf101-172">Attribute</span></span>|<span data-ttu-id="bf101-173">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-173">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="bf101-174">Musí mít hodnotu false (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bf101-174">Must be false (default).</span></span>|  
|`block`|<span data-ttu-id="bf101-175">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-175">Forbidden.</span></span>|  
|`final`|<span data-ttu-id="bf101-176">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-176">Ignored.</span></span>|  
|`id`|<span data-ttu-id="bf101-177">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-177">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="bf101-178">Musí mít hodnotu false (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bf101-178">Must be false (default).</span></span>|  
|`name`|<span data-ttu-id="bf101-179">Podporované a mapované na název kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="bf101-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="bf101-180">Pokud v názvu tečky, je proveden pokus o namapovat typ vnitřní typu.</span><span class="sxs-lookup"><span data-stu-id="bf101-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="bf101-181">Například komplexní typ s názvem `A.B` mapuje kontraktu dat typ, který je vnitřní druh typu s názvem kontraktu dat. `A`, ale jenom v případě, že tyto údaje smlouvy typu existuje.</span><span class="sxs-lookup"><span data-stu-id="bf101-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="bf101-182">Více než jedné úrovně vnoření je možné: například `A.B.C` může být vnitřní typ, ale jenom v případě `A` a `A.B` obě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="bf101-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|  
  
### <a name="xscomplextype-contents"></a><span data-ttu-id="bf101-183">\<xs:complexType >: obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-183">\<xs:complexType>: contents</span></span>  
  
|<span data-ttu-id="bf101-184">Obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-184">Contents</span></span>|<span data-ttu-id="bf101-185">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-185">Schema</span></span>|  
|--------------|------------|  
|`simpleContent`|<span data-ttu-id="bf101-186">Rozšíření jsou zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="bf101-187">Omezení je povoleno pouze ze `anySimpleType`.</span><span class="sxs-lookup"><span data-stu-id="bf101-187">Restriction is allowed only from `anySimpleType`.</span></span>|  
|`complexContent`|<span data-ttu-id="bf101-188">Podporováno.</span><span class="sxs-lookup"><span data-stu-id="bf101-188">Supported.</span></span> <span data-ttu-id="bf101-189">Najdete v části "Dědičnosti".</span><span class="sxs-lookup"><span data-stu-id="bf101-189">See "Inheritance".</span></span>|  
|`group`|<span data-ttu-id="bf101-190">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-190">Forbidden.</span></span>|  
|`all`|<span data-ttu-id="bf101-191">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-191">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="bf101-192">Je zakázané</span><span class="sxs-lookup"><span data-stu-id="bf101-192">Forbidden</span></span>|  
|`sequence`|<span data-ttu-id="bf101-193">Nepodporuje mapuje datových členů sady kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="bf101-193">Supported, maps to data members of a data contract.</span></span>|  
|`attribute`|<span data-ttu-id="bf101-194">Je zakázané, i v případě použití = "prohibited" (s jedinou výjimkou).</span><span class="sxs-lookup"><span data-stu-id="bf101-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="bf101-195">Jsou podporovány pouze volitelných atributů z oboru názvů schématu standardní serializace.</span><span class="sxs-lookup"><span data-stu-id="bf101-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="bf101-196">Budou se nemapují do datových členů v kontrakt dat programovací model.</span><span class="sxs-lookup"><span data-stu-id="bf101-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="bf101-197">V současné době pouze jeden takový atribut má význam a popsané v části ISerializable.</span><span class="sxs-lookup"><span data-stu-id="bf101-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="bf101-198">Všechny další se ignorují.</span><span class="sxs-lookup"><span data-stu-id="bf101-198">All others are ignored.</span></span>|  
|`attributeGroup`|<span data-ttu-id="bf101-199">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-199">Forbidden.</span></span> <span data-ttu-id="bf101-200">Ve verzi v1 WCF `DataContractSerializer` ignoruje přítomnost `attributeGroup` uvnitř `xs:complexType`.</span><span class="sxs-lookup"><span data-stu-id="bf101-200">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|  
|`anyAttribute`|<span data-ttu-id="bf101-201">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-201">Forbidden.</span></span>|  
|<span data-ttu-id="bf101-202">(prázdný)</span><span class="sxs-lookup"><span data-stu-id="bf101-202">(empty)</span></span>|<span data-ttu-id="bf101-203">Mapuje kontraktu dat bez členů data.</span><span class="sxs-lookup"><span data-stu-id="bf101-203">Maps to a data contract with no data members.</span></span>|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="bf101-204">\<: Sequence > složitý typ: atributy</span><span class="sxs-lookup"><span data-stu-id="bf101-204">\<xs:sequence> in a complex type: attributes</span></span>  
  
|<span data-ttu-id="bf101-205">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf101-205">Attribute</span></span>|<span data-ttu-id="bf101-206">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-206">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="bf101-207">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-207">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="bf101-208">Musí být 1 (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bf101-208">Must be 1 (default).</span></span>|  
|`minOccurs`|<span data-ttu-id="bf101-209">Musí být 1 (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bf101-209">Must be 1 (default).</span></span>|  
  
### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="bf101-210">\<: Sequence > složitý typ: obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-210">\<xs:sequence> in a complex type: contents</span></span>  
  
|<span data-ttu-id="bf101-211">Obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-211">Contents</span></span>|<span data-ttu-id="bf101-212">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-212">Schema</span></span>|  
|--------------|------------|  
|`element`|<span data-ttu-id="bf101-213">Každá instance se mapuje na člena.</span><span class="sxs-lookup"><span data-stu-id="bf101-213">Each instance maps to a data member.</span></span>|  
|`group`|<span data-ttu-id="bf101-214">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-214">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="bf101-215">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-215">Forbidden.</span></span>|  
|`sequence`|<span data-ttu-id="bf101-216">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-216">Forbidden.</span></span>|  
|`any`|<span data-ttu-id="bf101-217">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-217">Forbidden.</span></span>|  
|<span data-ttu-id="bf101-218">(prázdný)</span><span class="sxs-lookup"><span data-stu-id="bf101-218">(empty)</span></span>|<span data-ttu-id="bf101-219">Mapuje kontraktu dat bez členů data.</span><span class="sxs-lookup"><span data-stu-id="bf101-219">Maps to a data contract with no data members.</span></span>|  
  
## <a name="elements--xselement"></a><span data-ttu-id="bf101-220">Elementy – \<xs:element ></span><span class="sxs-lookup"><span data-stu-id="bf101-220">Elements – \<xs:element></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="bf101-221">Obecné informace</span><span class="sxs-lookup"><span data-stu-id="bf101-221">General Information</span></span>  
 <span data-ttu-id="bf101-222">`<xs:element>` může dojít v následujících kontextech:</span><span class="sxs-lookup"><span data-stu-id="bf101-222">`<xs:element>` can occur in the following contexts:</span></span>  
  
-   <span data-ttu-id="bf101-223">Může dojít v rámci `<xs:sequence>`, který popisuje členem data kontraktu regulární dat (bez kolekce).</span><span class="sxs-lookup"><span data-stu-id="bf101-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="bf101-224">V takovém případě `maxOccurs` atributu musí být 1.</span><span class="sxs-lookup"><span data-stu-id="bf101-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="bf101-225">(Není povolena hodnota 0).</span><span class="sxs-lookup"><span data-stu-id="bf101-225">(A value of 0 is not allowed).</span></span>  
  
-   <span data-ttu-id="bf101-226">Může dojít v rámci `<xs:sequence>`, který popisuje členem data kontraktu dat kolekce.</span><span class="sxs-lookup"><span data-stu-id="bf101-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="bf101-227">V takovém případě `maxOccurs` atributu musí být větší než 1 nebo "bez vazby".</span><span class="sxs-lookup"><span data-stu-id="bf101-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>  
  
-   <span data-ttu-id="bf101-228">Může dojít v rámci `<xs:schema>` jako globální Element deklarace (NĚNÁ).</span><span class="sxs-lookup"><span data-stu-id="bf101-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="bf101-229">\<xs:element > s maxOccurs = 1 v rámci \<: Sequence > (datové členy)</span><span class="sxs-lookup"><span data-stu-id="bf101-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>  
  
|<span data-ttu-id="bf101-230">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf101-230">Attribute</span></span>|<span data-ttu-id="bf101-231">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-231">Schema</span></span>|  
|---------------|------------|  
|`ref`|<span data-ttu-id="bf101-232">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-232">Forbidden.</span></span>|  
|`name`|<span data-ttu-id="bf101-233">Nepodporuje mapuje název člena data.</span><span class="sxs-lookup"><span data-stu-id="bf101-233">Supported, maps to the data member name.</span></span>|  
|`type`|<span data-ttu-id="bf101-234">Podporované, zadejte mapuje datový člen.</span><span class="sxs-lookup"><span data-stu-id="bf101-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="bf101-235">Další informace najdete v tématu typ nebo primitivní mapování.</span><span class="sxs-lookup"><span data-stu-id="bf101-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="bf101-236">Pokud není zadané (a element neobsahuje anonymní typ), `xs:anyType` se předpokládá.</span><span class="sxs-lookup"><span data-stu-id="bf101-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|  
|`block`|<span data-ttu-id="bf101-237">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-237">Ignored.</span></span>|  
|`default`|<span data-ttu-id="bf101-238">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-238">Forbidden.</span></span>|  
|`fixed`|<span data-ttu-id="bf101-239">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-239">Forbidden.</span></span>|  
|`form`|<span data-ttu-id="bf101-240">Musí být kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="bf101-240">Must be qualified.</span></span> <span data-ttu-id="bf101-241">Tento atribut lze nastavit pomocí `elementFormDefault` na `xs:schema`.</span><span class="sxs-lookup"><span data-stu-id="bf101-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|  
|`id`|<span data-ttu-id="bf101-242">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-242">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="bf101-243">1</span><span class="sxs-lookup"><span data-stu-id="bf101-243">1</span></span>|  
|`minOccurs`|<span data-ttu-id="bf101-244">Se mapuje <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost datového členu (`IsRequired` platí v případě `minOccurs` 1).</span><span class="sxs-lookup"><span data-stu-id="bf101-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|  
|`nillable`|<span data-ttu-id="bf101-245">Mapování typu ovlivňuje.</span><span class="sxs-lookup"><span data-stu-id="bf101-245">Affects type mapping.</span></span> <span data-ttu-id="bf101-246">V tématu typ nebo primitivní mapování.</span><span class="sxs-lookup"><span data-stu-id="bf101-246">See Type/primitive mapping.</span></span>|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="bf101-247">\<xs:element > s maxOccurs > 1 v rámci \<: Sequence > (kolekce)</span><span class="sxs-lookup"><span data-stu-id="bf101-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>  
  
-   <span data-ttu-id="bf101-248">Se mapuje <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bf101-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>  
  
-   <span data-ttu-id="bf101-249">V kolekci typů je povolen pouze jeden xs:element v rámci: Sequence.</span><span class="sxs-lookup"><span data-stu-id="bf101-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>  
  
 <span data-ttu-id="bf101-250">Kolekce může být z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="bf101-250">Collections can be of the following types:</span></span>  
  
-   <span data-ttu-id="bf101-251">Regulární kolekce (například polí).</span><span class="sxs-lookup"><span data-stu-id="bf101-251">Regular collections (for example, arrays).</span></span>  
  
-   <span data-ttu-id="bf101-252">Kolekce slovníku (mapování jednu hodnotu na jiný; například <xref:System.Collections.Hashtable>).</span><span class="sxs-lookup"><span data-stu-id="bf101-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>  
  
-   <span data-ttu-id="bf101-253">Jediným rozdílem mezi slovník a pole typu dvojice klíč/hodnota je v generované programovací model.</span><span class="sxs-lookup"><span data-stu-id="bf101-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="bf101-254">Není schématu poznámky mechanismus, který slouží k označení, že je daný typ kolekce slovníku.</span><span class="sxs-lookup"><span data-stu-id="bf101-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>  
  
 <span data-ttu-id="bf101-255">Pravidla pro `ref`, `block`, `default`, `fixed`, `form`, a `id` atributy jsou stejné jako pro případ jiné kolekce.</span><span class="sxs-lookup"><span data-stu-id="bf101-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="bf101-256">Ostatní atributy patří v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="bf101-256">Other attributes include those in the following table.</span></span>  
  
|<span data-ttu-id="bf101-257">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf101-257">Attribute</span></span>|<span data-ttu-id="bf101-258">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-258">Schema</span></span>|  
|---------------|------------|  
|`name`|<span data-ttu-id="bf101-259">Podporovaná, je přiřazen <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> vlastnost `CollectionDataContractAttribute` atribut.</span><span class="sxs-lookup"><span data-stu-id="bf101-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|  
|`type`|<span data-ttu-id="bf101-260">Nepodporuje mapuje na typ uložené v kolekci.</span><span class="sxs-lookup"><span data-stu-id="bf101-260">Supported, maps to the type stored in the collection.</span></span>|  
|`maxOccurs`|<span data-ttu-id="bf101-261">Větší než 1 nebo "bez vazby".</span><span class="sxs-lookup"><span data-stu-id="bf101-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="bf101-262">Schéma řadiče domény by měli používat "bez vazby".</span><span class="sxs-lookup"><span data-stu-id="bf101-262">The DC schema should use "unbounded".</span></span>|  
|`minOccurs`|<span data-ttu-id="bf101-263">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-263">Ignored.</span></span>|  
|`nillable`|<span data-ttu-id="bf101-264">Mapování typu ovlivňuje.</span><span class="sxs-lookup"><span data-stu-id="bf101-264">Affects type mapping.</span></span> <span data-ttu-id="bf101-265">Tento atribut je ignorován pro kolekce slovníku.</span><span class="sxs-lookup"><span data-stu-id="bf101-265">This attribute is ignored for dictionary collections.</span></span>|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="bf101-266">\<xs:element > v rámci \<xs:schema > globální deklarace Element</span><span class="sxs-lookup"><span data-stu-id="bf101-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>  
  
-   <span data-ttu-id="bf101-267">Globální Element deklarace (NĚNÁ), má se stejným názvem a oboru názvů jako typu ve schématu, nebo anonymní typ uvnitř sebe, který definuje říká, že je možné přidružit s typem.</span><span class="sxs-lookup"><span data-stu-id="bf101-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>  
  
-   <span data-ttu-id="bf101-268">Export schématu: přidružené GEDs jsou generovány pro každý typ generovaného, jednoduché a komplexní.</span><span class="sxs-lookup"><span data-stu-id="bf101-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>  
  
-   <span data-ttu-id="bf101-269">Deserializace/serializace: přidružené GEDs jsou použity jako kořenové elementy pro typ.</span><span class="sxs-lookup"><span data-stu-id="bf101-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>  
  
-   <span data-ttu-id="bf101-270">Import schématu: přidružené GEDs není vyžadován a jsou ignorovány, pokud se podle následujících pravidel (Pokud se definování typů).</span><span class="sxs-lookup"><span data-stu-id="bf101-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>  
  
|<span data-ttu-id="bf101-271">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf101-271">Attribute</span></span>|<span data-ttu-id="bf101-272">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-272">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="bf101-273">Musí mít hodnotu false pro přidružené GEDs.</span><span class="sxs-lookup"><span data-stu-id="bf101-273">Must be false for associated GEDs.</span></span>|  
|`block`|<span data-ttu-id="bf101-274">Je zakázané v přidružené GEDs.</span><span class="sxs-lookup"><span data-stu-id="bf101-274">Forbidden in associated GEDs.</span></span>|  
|`default`|<span data-ttu-id="bf101-275">Je zakázané v přidružené GEDs.</span><span class="sxs-lookup"><span data-stu-id="bf101-275">Forbidden in associated GEDs.</span></span>|  
|`final`|<span data-ttu-id="bf101-276">Musí mít hodnotu false pro přidružené GEDs.</span><span class="sxs-lookup"><span data-stu-id="bf101-276">Must be false for associated GEDs.</span></span>|  
|`fixed`|<span data-ttu-id="bf101-277">Je zakázané v přidružené GEDs.</span><span class="sxs-lookup"><span data-stu-id="bf101-277">Forbidden in associated GEDs.</span></span>|  
|`id`|<span data-ttu-id="bf101-278">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-278">Ignored.</span></span>|  
|`name`|<span data-ttu-id="bf101-279">Podporováno.</span><span class="sxs-lookup"><span data-stu-id="bf101-279">Supported.</span></span> <span data-ttu-id="bf101-280">Viz definice přidružené GEDs.</span><span class="sxs-lookup"><span data-stu-id="bf101-280">See the definition of associated GEDs.</span></span>|  
|`nillable`|<span data-ttu-id="bf101-281">Musí být pro přidružené GEDs na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="bf101-281">Must be true for associated GEDs.</span></span>|  
|`substitutionGroup`|<span data-ttu-id="bf101-282">Je zakázané v přidružené GEDs.</span><span class="sxs-lookup"><span data-stu-id="bf101-282">Forbidden in associated GEDs.</span></span>|  
|`type`|<span data-ttu-id="bf101-283">Podporované a musí odpovídat typ přidružené přidružené GEDs (pokud element obsahuje anonymní typ).</span><span class="sxs-lookup"><span data-stu-id="bf101-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|  
  
### <a name="xselement-contents"></a><span data-ttu-id="bf101-284">\<xs:element >: obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-284">\<xs:element>: contents</span></span>  
  
|<span data-ttu-id="bf101-285">Obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-285">Contents</span></span>|<span data-ttu-id="bf101-286">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-286">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="bf101-287">Supported.\*</span><span class="sxs-lookup"><span data-stu-id="bf101-287">Supported.\*</span></span>|  
|`complexType`|<span data-ttu-id="bf101-288">Supported.\*</span><span class="sxs-lookup"><span data-stu-id="bf101-288">Supported.\*</span></span>|  
|`unique`|<span data-ttu-id="bf101-289">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-289">Ignored.</span></span>|  
|`key`|<span data-ttu-id="bf101-290">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-290">Ignored.</span></span>|  
|`keyref`|<span data-ttu-id="bf101-291">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-291">Ignored.</span></span>|  
|<span data-ttu-id="bf101-292">(prázdný)</span><span class="sxs-lookup"><span data-stu-id="bf101-292">(blank)</span></span>|<span data-ttu-id="bf101-293">Podporováno.</span><span class="sxs-lookup"><span data-stu-id="bf101-293">Supported.</span></span>|  
  
 <span data-ttu-id="bf101-294">\* Při použití `simpleType` a `complexType,` mapování pro anonymní typy je stejné jako anonymní typy, s tím rozdílem, že neexistuje žádná kontrakty anonymní dat, a tudíž vytvoření kontraktu dat s názvem s názvem odvozené od názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="bf101-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="bf101-295">Pravidla pro anonymní typy jsou v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="bf101-295">The rules for anonymous types are in the following list:</span></span>  
  
-   <span data-ttu-id="bf101-296">Podrobnosti implementace WCF: Pokud `xs:element` název neobsahuje období, anonymního typu se mapuje na typ vnitřní, vnější datového typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="bf101-296">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="bf101-297">Pokud název obsahuje tečky, výsledný typ kontraktu dat je nezávislá (není vnitřní typ).</span><span class="sxs-lookup"><span data-stu-id="bf101-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>  
  
-   <span data-ttu-id="bf101-298">Název kontraktu generované datové vnitřní typu je název kontraktu dat vnější typu, za nímž následuje období, název elementu a řetězce "Typ".</span><span class="sxs-lookup"><span data-stu-id="bf101-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>  
  
-   <span data-ttu-id="bf101-299">Pokud data smluvním vztahu se tento název již existuje, název je jedinečný připojením "1", "2", "3", a tak dále, dokud nebude vytvořen jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="bf101-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>  
  
## <a name="simple-types---xssimpletype"></a><span data-ttu-id="bf101-300">Jednoduché typy - \<xs:simpleType ></span><span class="sxs-lookup"><span data-stu-id="bf101-300">Simple Types - \<xs:simpleType></span></span>  
  
### <a name="xssimpletype-attributes"></a><span data-ttu-id="bf101-301">\<xs:simpleType >: atributy</span><span class="sxs-lookup"><span data-stu-id="bf101-301">\<xs:simpleType>: attributes</span></span>  
  
|<span data-ttu-id="bf101-302">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf101-302">Attribute</span></span>|<span data-ttu-id="bf101-303">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-303">Schema</span></span>|  
|---------------|------------|  
|`final`|<span data-ttu-id="bf101-304">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-304">Ignored.</span></span>|  
|`id`|<span data-ttu-id="bf101-305">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-305">Ignored.</span></span>|  
|`name`|<span data-ttu-id="bf101-306">Podporované, mapuje data název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="bf101-306">Supported, maps to the data contract name.</span></span>|  
  
### <a name="xssimpletype-contents"></a><span data-ttu-id="bf101-307">\<xs:simpleType >: obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-307">\<xs:simpleType>: contents</span></span>  
  
|<span data-ttu-id="bf101-308">Obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-308">Contents</span></span>|<span data-ttu-id="bf101-309">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-309">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="bf101-310">Podporováno.</span><span class="sxs-lookup"><span data-stu-id="bf101-310">Supported.</span></span> <span data-ttu-id="bf101-311">Kontrakty se mapuje na dat výčtu.</span><span class="sxs-lookup"><span data-stu-id="bf101-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="bf101-312">Tento atribut je ignorován, pokud neodpovídá vzoru výčtu.</span><span class="sxs-lookup"><span data-stu-id="bf101-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="bf101-313">Najdete v článku `xs:simpleType` části omezení.</span><span class="sxs-lookup"><span data-stu-id="bf101-313">See the `xs:simpleType` restrictions section.</span></span>|  
|`list`|<span data-ttu-id="bf101-314">Podporováno.</span><span class="sxs-lookup"><span data-stu-id="bf101-314">Supported.</span></span> <span data-ttu-id="bf101-315">Mapuje příznak kontrakty dat výčtu.</span><span class="sxs-lookup"><span data-stu-id="bf101-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="bf101-316">Najdete v článku `xs:simpleType` uvádí oddíl.</span><span class="sxs-lookup"><span data-stu-id="bf101-316">See the `xs:simpleType` lists section.</span></span>|  
|`union`|<span data-ttu-id="bf101-317">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-317">Forbidden.</span></span>|  
  
### <a name="xsrestriction"></a><span data-ttu-id="bf101-318">\<xs:restriction ></span><span class="sxs-lookup"><span data-stu-id="bf101-318">\<xs:restriction></span></span>  
  
-   <span data-ttu-id="bf101-319">Komplexní typ omezení jsou podporovány pouze pro základní = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="bf101-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>  
  
-   <span data-ttu-id="bf101-320">Jednoduchý typ omezení u `xs:string` které nemají žádné omezení omezující než `xs:enumeration` jsou namapované na kontrakty dat výčtu.</span><span class="sxs-lookup"><span data-stu-id="bf101-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>  
  
-   <span data-ttu-id="bf101-321">Další omezení jednoduchého typu jsou namapované na typy, které omezují.</span><span class="sxs-lookup"><span data-stu-id="bf101-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="bf101-322">Například omezení u `xs:int` mapuje na typ integer, stejně jako `xs:int` sám nemá.</span><span class="sxs-lookup"><span data-stu-id="bf101-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="bf101-323">Další informace o mapování primitivní typ najdete v části typ nebo primitivní mapování.</span><span class="sxs-lookup"><span data-stu-id="bf101-323">For more information about primitive type mapping, see Type/primitive mapping.</span></span>  
  
### <a name="xsrestriction-attributes"></a><span data-ttu-id="bf101-324">\<xs:restriction >: atributy</span><span class="sxs-lookup"><span data-stu-id="bf101-324">\<xs:restriction>: attributes</span></span>  
  
|<span data-ttu-id="bf101-325">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf101-325">Attribute</span></span>|<span data-ttu-id="bf101-326">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-326">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="bf101-327">Musí být podporovaná jednoduchého typu nebo `xs:anyType`.</span><span class="sxs-lookup"><span data-stu-id="bf101-327">Must be a supported simple type or `xs:anyType`.</span></span>|  
|`id`|<span data-ttu-id="bf101-328">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-328">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="bf101-329">\<xs:restriction > pro všechny další případy: obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-329">\<xs:restriction> for all other cases: contents</span></span>  
  
|<span data-ttu-id="bf101-330">Obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-330">Contents</span></span>|<span data-ttu-id="bf101-331">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-331">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="bf101-332">Pokud je k dispozici, musí být odvozen z podporovaných primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="bf101-332">If present, must be derived from a supported primitive type.</span></span>|  
|`minExclusive`|<span data-ttu-id="bf101-333">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-333">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="bf101-334">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-334">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="bf101-335">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-335">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="bf101-336">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-336">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="bf101-337">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-337">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="bf101-338">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-338">Ignored.</span></span>|  
|`length`|<span data-ttu-id="bf101-339">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-339">Ignored.</span></span>|  
|`minLength`|<span data-ttu-id="bf101-340">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-340">Ignored.</span></span>|  
|`maxLength`|<span data-ttu-id="bf101-341">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-341">Ignored.</span></span>|  
|`enumeration`|<span data-ttu-id="bf101-342">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-342">Ignored.</span></span>|  
|`whiteSpace`|<span data-ttu-id="bf101-343">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-343">Ignored.</span></span>|  
|`pattern`|<span data-ttu-id="bf101-344">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-344">Ignored.</span></span>|  
|<span data-ttu-id="bf101-345">(prázdný)</span><span class="sxs-lookup"><span data-stu-id="bf101-345">(blank)</span></span>|<span data-ttu-id="bf101-346">Podporováno.</span><span class="sxs-lookup"><span data-stu-id="bf101-346">Supported.</span></span>|  
  
## <a name="enumeration"></a><span data-ttu-id="bf101-347">Výčet</span><span class="sxs-lookup"><span data-stu-id="bf101-347">Enumeration</span></span>  
  
### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="bf101-348">\<xs:restriction > pro výčty: atributy</span><span class="sxs-lookup"><span data-stu-id="bf101-348">\<xs:restriction> for enumerations: attributes</span></span>  
  
|<span data-ttu-id="bf101-349">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf101-349">Attribute</span></span>|<span data-ttu-id="bf101-350">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-350">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="bf101-351">Pokud existuje, musí být `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="bf101-351">If present, must be `xs:string`.</span></span>|  
|`id`|<span data-ttu-id="bf101-352">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-352">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="bf101-353">\<xs:restriction > pro výčty: obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-353">\<xs:restriction> for enumerations: contents</span></span>  
  
|<span data-ttu-id="bf101-354">Obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-354">Contents</span></span>|<span data-ttu-id="bf101-355">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-355">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="bf101-356">Pokud je k dispozici, musí být omezení enumeration podporována kontrakt dat (této části).</span><span class="sxs-lookup"><span data-stu-id="bf101-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|  
|`minExclusive`|<span data-ttu-id="bf101-357">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-357">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="bf101-358">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-358">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="bf101-359">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-359">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="bf101-360">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-360">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="bf101-361">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-361">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="bf101-362">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-362">Ignored.</span></span>|  
|`length`|<span data-ttu-id="bf101-363">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-363">Forbidden.</span></span>|  
|`minLength`|<span data-ttu-id="bf101-364">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-364">Forbidden.</span></span>|  
|`maxLength`|<span data-ttu-id="bf101-365">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-365">Forbidden.</span></span>|  
|`enumeration`|<span data-ttu-id="bf101-366">Podporováno.</span><span class="sxs-lookup"><span data-stu-id="bf101-366">Supported.</span></span> <span data-ttu-id="bf101-367">Je ignorován výčtu "id" a "value" mapuje název hodnoty v kontraktu dat výčtu.</span><span class="sxs-lookup"><span data-stu-id="bf101-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|  
|`whiteSpace`|<span data-ttu-id="bf101-368">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-368">Forbidden.</span></span>|  
|`pattern`|<span data-ttu-id="bf101-369">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-369">Forbidden.</span></span>|  
|<span data-ttu-id="bf101-370">(prázdný)</span><span class="sxs-lookup"><span data-stu-id="bf101-370">(empty)</span></span>|<span data-ttu-id="bf101-371">Nepodporuje mapuje na typ prázdný výčet.</span><span class="sxs-lookup"><span data-stu-id="bf101-371">Supported, maps to empty enumeration type.</span></span>|  
  
 <span data-ttu-id="bf101-372">Následující kód ukazuje výčet tříd jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="bf101-372">The following code shows a C# enumeration class.</span></span>  
  
```  
public enum MyEnum  
{  
   first = 3,  
   second = 4,  
   third =5  
```  
  
 <span data-ttu-id="bf101-373">}</span><span class="sxs-lookup"><span data-stu-id="bf101-373">}</span></span>  
  
 <span data-ttu-id="bf101-374">Tato třída se mapuje na schéma následující pomocí `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="bf101-374">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="bf101-375">Pokud hodnoty výčtu začínají 1, `xs:annotation` nejsou generované bloky.</span><span class="sxs-lookup"><span data-stu-id="bf101-375">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>  
  
```xml  
<xs:simpleType name="MyEnum">  
<xs:restriction base="xs:string">  
 <xs:enumeration value="first">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     3  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
 <xs:enumeration value="second">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     4  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
</xs:restriction>  
</xs:simpleType>  
```  
  
### <a name="xslist"></a><span data-ttu-id="bf101-376">\<xs:list></span><span class="sxs-lookup"><span data-stu-id="bf101-376">\<xs:list></span></span>  
 <span data-ttu-id="bf101-377">`DataContractSerializer` Výčtové typy mapy označené jako `System.FlagsAttribute` k `xs:list` odvozené z `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="bf101-377">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="bf101-378">Žádný jiný `xs:list` rozdíly jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="bf101-378">No other `xs:list` variations are supported.</span></span>  
  
### <a name="xslist-attributes"></a><span data-ttu-id="bf101-379">\<xs:list >: atributy</span><span class="sxs-lookup"><span data-stu-id="bf101-379">\<xs:list>: attributes</span></span>  
  
|<span data-ttu-id="bf101-380">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf101-380">Attribute</span></span>|<span data-ttu-id="bf101-381">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-381">Schema</span></span>|  
|---------------|------------|  
|`itemType`|<span data-ttu-id="bf101-382">Je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bf101-382">Forbidden.</span></span>|  
|`id`|<span data-ttu-id="bf101-383">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-383">Ignored.</span></span>|  
  
### <a name="xslist-contents"></a><span data-ttu-id="bf101-384">\<xs:list >: obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-384">\<xs:list>: contents</span></span>  
  
|<span data-ttu-id="bf101-385">Obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-385">Contents</span></span>|<span data-ttu-id="bf101-386">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-386">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="bf101-387">Musí být omezení `xs:string` pomocí `xs:enumeration` omezující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bf101-387">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|  
  
 <span data-ttu-id="bf101-388">Pokud hodnota výčtu nedodrží druhou mocninou 2 postupu (výchozí nastavení pro příznaky), hodnota je uložena v `xs:annotation/xs:appInfo/ser:EnumerationValue` elementu.</span><span class="sxs-lookup"><span data-stu-id="bf101-388">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>  
  
 <span data-ttu-id="bf101-389">Následující kód například příznaky typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="bf101-389">For example, the following code flags an enumeration type.</span></span>  
  
```  
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
  
 <span data-ttu-id="bf101-390">Tento typ se mapuje na následující schéma.</span><span class="sxs-lookup"><span data-stu-id="bf101-390">This type maps to the following schema.</span></span>  
  
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
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">16</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
          <xs:enumeration value="AuthWindowsLiveID">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">64</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:list>  
  </xs:simpleType>  
```  
  
## <a name="inheritance"></a><span data-ttu-id="bf101-391">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="bf101-391">Inheritance</span></span>  
  
### <a name="general-rules"></a><span data-ttu-id="bf101-392">Obecná pravidla</span><span class="sxs-lookup"><span data-stu-id="bf101-392">General rules</span></span>  
 <span data-ttu-id="bf101-393">Kontrakt dat může dědit vlastnosti z jiné smlouvy data.</span><span class="sxs-lookup"><span data-stu-id="bf101-393">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="bf101-394">Tyto smlouvy data namapovat na základní a jsou odvozené typy rozšíření pomocí `<xs:extension>` konstrukce schématu XML.</span><span class="sxs-lookup"><span data-stu-id="bf101-394">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>  
  
 <span data-ttu-id="bf101-395">Kontrakt dat nemůže Zdědit z kontraktu dat kolekce.</span><span class="sxs-lookup"><span data-stu-id="bf101-395">A data contract cannot inherit from a collection data contract.</span></span>  
  
 <span data-ttu-id="bf101-396">Například následující kód je kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="bf101-396">For example, the following code is a data contract.</span></span>  
  
```  
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
  
 <span data-ttu-id="bf101-397">Tento kontrakt dat se mapuje na typ deklarace schématu XML.</span><span class="sxs-lookup"><span data-stu-id="bf101-397">This data contract maps to the following XML Schema type declaration.</span></span>  
  
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
  
### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="bf101-398">\<xs:complexContent >: atributy</span><span class="sxs-lookup"><span data-stu-id="bf101-398">\<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="bf101-399">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf101-399">Attribute</span></span>|<span data-ttu-id="bf101-400">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-400">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="bf101-401">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-401">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="bf101-402">Musí mít hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="bf101-402">Must be false.</span></span>|  
  
### <a name="xscomplexcontent-contents"></a><span data-ttu-id="bf101-403">\<xs:complexContent >: obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-403">\<xs:complexContent>: contents</span></span>  
  
|<span data-ttu-id="bf101-404">Obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-404">Contents</span></span>|<span data-ttu-id="bf101-405">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-405">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="bf101-406">Zakázáno, s výjimkou základní = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="bf101-406">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="bf101-407">K tomu je ekvivalentní umístění obsahu `xs:restriction` přímo v kontejneru systému `xs:complexContent`.</span><span class="sxs-lookup"><span data-stu-id="bf101-407">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|  
|`extension`|<span data-ttu-id="bf101-408">Podporováno.</span><span class="sxs-lookup"><span data-stu-id="bf101-408">Supported.</span></span> <span data-ttu-id="bf101-409">Mapuje data smluvním vztahu dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="bf101-409">Maps to data contract inheritance.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="bf101-410">\<xs:Extension > v \<xs:complexContent >: atributy</span><span class="sxs-lookup"><span data-stu-id="bf101-410">\<xs:extension> in \<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="bf101-411">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf101-411">Attribute</span></span>|<span data-ttu-id="bf101-412">Schéma</span><span class="sxs-lookup"><span data-stu-id="bf101-412">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="bf101-413">Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="bf101-413">Ignored.</span></span>|  
|`base`|<span data-ttu-id="bf101-414">Podporováno.</span><span class="sxs-lookup"><span data-stu-id="bf101-414">Supported.</span></span> <span data-ttu-id="bf101-415">Mapuje kontrakt základní dat zadejte, zda tento typ dědí od.</span><span class="sxs-lookup"><span data-stu-id="bf101-415">Maps to the base data contract type that this type inherits from.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="bf101-416">\<xs:Extension > v \<xs:complexContent >: obsah</span><span class="sxs-lookup"><span data-stu-id="bf101-416">\<xs:extension> in \<xs:complexContent>: contents</span></span>  
 <span data-ttu-id="bf101-417">Pravidla jsou stejné jako u `<xs:complexType>` obsah.</span><span class="sxs-lookup"><span data-stu-id="bf101-417">The rules are the same as for `<xs:complexType>` contents.</span></span>  
  
 <span data-ttu-id="bf101-418">Pokud `<xs:sequence>` je k dispozici, jeho členských elementy mapy členům další data, které se nacházejí v kontraktu odvozené data.</span><span class="sxs-lookup"><span data-stu-id="bf101-418">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>  
  
 <span data-ttu-id="bf101-419">Pokud odvozený typ obsahuje element se stejným názvem jako element v základním typu, deklaraci duplicitní element se mapuje na člena s názvem, který se vygeneruje být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="bf101-419">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="bf101-420">Kladná celá čísla se přidají k názvu data člena ("Člen1", "člen2" a tak dále) až do nalezení jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="bf101-420">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="bf101-421">Na druhé straně:</span><span class="sxs-lookup"><span data-stu-id="bf101-421">Conversely:</span></span>  
  
-   <span data-ttu-id="bf101-422">Kontrakt odvozené dat má datový člen se stejným názvem a typem jako člena dat v kontraktu základní data `DataContractSerializer` generuje tento odpovídající element v odvozeném typu.</span><span class="sxs-lookup"><span data-stu-id="bf101-422">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>  
  
-   <span data-ttu-id="bf101-423">Pokud má datový člen se stejným názvem jako člena dat ve kontraktu základní data, ale jiný typ kontraktu odvozené data `DataContractSerializer` importuje schéma s elementem typu `xs:anyType` v základním typu a odvozený typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="bf101-423">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="bf101-424">Původní název typu se zachová, i v `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span><span class="sxs-lookup"><span data-stu-id="bf101-424">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>  
  
 <span data-ttu-id="bf101-425">Obě varianty může vést ke schématu s nejednoznačný modelu obsahu, což závisí v řádu příslušné datové členy.</span><span class="sxs-lookup"><span data-stu-id="bf101-425">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>  
  
## <a name="typeprimitive-mapping"></a><span data-ttu-id="bf101-426">Typ nebo primitivní mapování</span><span class="sxs-lookup"><span data-stu-id="bf101-426">Type/primitive mapping</span></span>  
 <span data-ttu-id="bf101-427">`DataContractSerializer` Používá následující mapování pro primitivní typy schématu XML.</span><span class="sxs-lookup"><span data-stu-id="bf101-427">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>  
  
|<span data-ttu-id="bf101-428">Typ XSD</span><span class="sxs-lookup"><span data-stu-id="bf101-428">XSD type</span></span>|<span data-ttu-id="bf101-429">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="bf101-429">.NET type</span></span>|  
|--------------|---------------|  
|`anyType`|<span data-ttu-id="bf101-430"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="bf101-430"><xref:System.Object>.</span></span>|  
|`anySimpleType`|<span data-ttu-id="bf101-431"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-431"><xref:System.String>.</span></span>|  
|`duration`|<span data-ttu-id="bf101-432"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="bf101-432"><xref:System.TimeSpan>.</span></span>|  
|`dateTime`|<span data-ttu-id="bf101-433"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="bf101-433"><xref:System.DateTime>.</span></span>|  
|`dateTimeOffset`|<span data-ttu-id="bf101-434"><xref:System.DateTime> a <xref:System.TimeSpan> posunu.</span><span class="sxs-lookup"><span data-stu-id="bf101-434"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="bf101-435">Najdete v části serializace DateTimeOffset níže.</span><span class="sxs-lookup"><span data-stu-id="bf101-435">See DateTimeOffset Serialization below.</span></span>|  
|`time`|<span data-ttu-id="bf101-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-436"><xref:System.String>.</span></span>|  
|`date`|<span data-ttu-id="bf101-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-437"><xref:System.String>.</span></span>|  
|`gYearMonth`|<span data-ttu-id="bf101-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-438"><xref:System.String>.</span></span>|  
|`gYear`|<span data-ttu-id="bf101-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-439"><xref:System.String>.</span></span>|  
|`gMonthDay`|<span data-ttu-id="bf101-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-440"><xref:System.String>.</span></span>|  
|`gDay`|<span data-ttu-id="bf101-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-441"><xref:System.String>.</span></span>|  
|`gMonth`|<span data-ttu-id="bf101-442"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-442"><xref:System.String>.</span></span>|  
|`boolean`|<xref:System.Boolean>|  
|`base64Binary`|<span data-ttu-id="bf101-443"><xref:System.Byte> Pole.</span><span class="sxs-lookup"><span data-stu-id="bf101-443"><xref:System.Byte> array.</span></span>|  
|`hexBinary`|<span data-ttu-id="bf101-444"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-444"><xref:System.String>.</span></span>|  
|`float`|<span data-ttu-id="bf101-445"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="bf101-445"><xref:System.Single>.</span></span>|  
|`double`|<span data-ttu-id="bf101-446"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="bf101-446"><xref:System.Double>.</span></span>|  
|`anyURI`|<span data-ttu-id="bf101-447"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="bf101-447"><xref:System.Uri>.</span></span>|  
|`QName`|<span data-ttu-id="bf101-448"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="bf101-448"><xref:System.Xml.XmlQualifiedName>.</span></span>|  
|`string`|<span data-ttu-id="bf101-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-449"><xref:System.String>.</span></span>|  
|`normalizedString`|<span data-ttu-id="bf101-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-450"><xref:System.String>.</span></span>|  
|`token`|<span data-ttu-id="bf101-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-451"><xref:System.String>.</span></span>|  
|`language`|<span data-ttu-id="bf101-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-452"><xref:System.String>.</span></span>|  
|`Name`|<span data-ttu-id="bf101-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-453"><xref:System.String>.</span></span>|  
|`NCName`|<span data-ttu-id="bf101-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-454"><xref:System.String>.</span></span>|  
|`ID`|<span data-ttu-id="bf101-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-455"><xref:System.String>.</span></span>|  
|`IDREF`|<span data-ttu-id="bf101-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-456"><xref:System.String>.</span></span>|  
|`IDREFS`|<span data-ttu-id="bf101-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-457"><xref:System.String>.</span></span>|  
|`ENTITY`|<span data-ttu-id="bf101-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-458"><xref:System.String>.</span></span>|  
|`ENTITIES`|<span data-ttu-id="bf101-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-459"><xref:System.String>.</span></span>|  
|`NMTOKEN`|<span data-ttu-id="bf101-460"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-460"><xref:System.String>.</span></span>|  
|`NMTOKENS`|<span data-ttu-id="bf101-461"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bf101-461"><xref:System.String>.</span></span>|  
|`decimal`|<span data-ttu-id="bf101-462"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="bf101-462"><xref:System.Decimal>.</span></span>|  
|`integer`|<span data-ttu-id="bf101-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="bf101-463"><xref:System.Int64>.</span></span>|  
|`nonPositiveInteger`|<span data-ttu-id="bf101-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="bf101-464"><xref:System.Int64>.</span></span>|  
|`negativeInteger`|<span data-ttu-id="bf101-465"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="bf101-465"><xref:System.Int64>.</span></span>|  
|`long`|<span data-ttu-id="bf101-466"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="bf101-466"><xref:System.Int64>.</span></span>|  
|`int`|<span data-ttu-id="bf101-467"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="bf101-467"><xref:System.Int32>.</span></span>|  
|`short`|<span data-ttu-id="bf101-468"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="bf101-468"><xref:System.Int16>.</span></span>|  
|`Byte`|<span data-ttu-id="bf101-469"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="bf101-469"><xref:System.SByte>.</span></span>|  
|`nonNegativeInteger`|<span data-ttu-id="bf101-470"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="bf101-470"><xref:System.Int64>.</span></span>|  
|`unsignedLong`|<span data-ttu-id="bf101-471"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="bf101-471"><xref:System.UInt64>.</span></span>|  
|`unsignedInt`|<span data-ttu-id="bf101-472"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="bf101-472"><xref:System.UInt32>.</span></span>|  
|`unsignedShort`|<span data-ttu-id="bf101-473"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="bf101-473"><xref:System.UInt16>.</span></span>|  
|`unsignedByte`|<span data-ttu-id="bf101-474"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="bf101-474"><xref:System.Byte>.</span></span>|  
|`positiveInteger`|<span data-ttu-id="bf101-475"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="bf101-475"><xref:System.Int64>.</span></span>|  
  
## <a name="iserializable-types-mapping"></a><span data-ttu-id="bf101-476">Typy iSerializable mapování</span><span class="sxs-lookup"><span data-stu-id="bf101-476">ISerializable types mapping</span></span>  
 <span data-ttu-id="bf101-477">V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, `ISerializable` byla zavedena jako obecné mechanismus pro serializaci objektů pro přenos trvalost nebo data.</span><span class="sxs-lookup"><span data-stu-id="bf101-477">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0, `ISerializable` was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="bf101-478">Existuje mnoho [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, které implementují `ISerializable` , které lze předat mezi aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="bf101-478">There are many [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="bf101-479">`DataContractSerializer` přirozeně poskytuje podporu pro `ISerializable` třídy.</span><span class="sxs-lookup"><span data-stu-id="bf101-479">`DataContractSerializer` naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="bf101-480">`DataContractSerializer` Mapuje `ISerializable` typy schémat implementace, které liší pouze QName (kvalifikovaný název) typu a jsou efektivně vlastnost kolekce.</span><span class="sxs-lookup"><span data-stu-id="bf101-480">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="bf101-481">Například `DataContractSerializer` mapuje <xref:System.Exception> na následující typ XSD v http://schemas.datacontract.org/2004/07/System oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bf101-481">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the http://schemas.datacontract.org/2004/07/System namespace.</span></span>  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 <span data-ttu-id="bf101-482">Volitelný atribut `ser:FactoryType` deklarované v serializaci kontraktu dat schématu odkazuje na třídu objektů factory, který může deserializovat daný typ.</span><span class="sxs-lookup"><span data-stu-id="bf101-482">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="bf101-483">Třídu objektů factory musí být součástí kolekce známé typy `DataContractSerializer` instance, používá.</span><span class="sxs-lookup"><span data-stu-id="bf101-483">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="bf101-484">Další informace o známé typy najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="bf101-484">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="datacontract-serialization-schema"></a><span data-ttu-id="bf101-485">Schéma serializace kontraktu</span><span class="sxs-lookup"><span data-stu-id="bf101-485">DataContract Serialization Schema</span></span>  
 <span data-ttu-id="bf101-486">Počet schémata exportované sadou `DataContractSerializer` použijte typy elementů a atributů z speciální obor názvů kontraktu serializace dat:</span><span class="sxs-lookup"><span data-stu-id="bf101-486">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>  
  
 http://schemas.microsoft.com/2003/10/Serialization  
  
 <span data-ttu-id="bf101-487">Toto je úplné deklarace schématu serializace dat kontrakt.</span><span class="sxs-lookup"><span data-stu-id="bf101-487">The following is a complete Data Contract Serialization schema declaration.</span></span>  
  
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
  
 <span data-ttu-id="bf101-488">Následující potřeba poznamenat:</span><span class="sxs-lookup"><span data-stu-id="bf101-488">The following should be noted:</span></span>  
  
-   <span data-ttu-id="bf101-489">`ser:char` Uvádíme představují znaky znakové sady Unicode typu <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="bf101-489">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>  
  
-   <span data-ttu-id="bf101-490">`valuespace` z `xs:duration` zkrátila seřazené sady tak, aby bylo možné namapovat na <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="bf101-490">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>  
  
-   <span data-ttu-id="bf101-491">`FactoryType` se používá v schémata exportovat z typů, které jsou odvozeny od <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="bf101-491">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="bf101-492">Import schémata bez kontraktu</span><span class="sxs-lookup"><span data-stu-id="bf101-492">Importing non-DataContract schemas</span></span>  
 <span data-ttu-id="bf101-493">`DataContractSerializer` má `ImportXmlTypes` možnost, povolíte import schémat, které nejsou v souladu s `DataContractSerializer` profil XSD (najdete v článku <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> vlastnost).</span><span class="sxs-lookup"><span data-stu-id="bf101-493">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="bf101-494">Nastavení této možnosti na `true` umožňuje přijetí nonkonformní typy schémat a jejich mapování pro následující implementaci <xref:System.Xml.Serialization.IXmlSerializable> zabalení pole <xref:System.Xml.XmlNode> (jenom název třídy se liší).</span><span class="sxs-lookup"><span data-stu-id="bf101-494">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>  
  
```  
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
  
## <a name="datetimeoffset-serialization"></a><span data-ttu-id="bf101-495">Serializace DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="bf101-495">DateTimeOffset Serialization</span></span>  
 <span data-ttu-id="bf101-496"><xref:System.DateTimeOffset> Nepovažuje primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="bf101-496">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="bf101-497">Místo toho je serializováno jako element komplexní se skládá ze dvou částí.</span><span class="sxs-lookup"><span data-stu-id="bf101-497">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="bf101-498">Představuje první část času a druhá část představuje posun od času.</span><span class="sxs-lookup"><span data-stu-id="bf101-498">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="bf101-499">V následujícím kódu je uveden příklad serializovaných DateTimeOffset hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bf101-499">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="bf101-500">Schéma je následující.</span><span class="sxs-lookup"><span data-stu-id="bf101-500">The schema is as follows.</span></span>  
  
```xml  
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">  
   <xs:complexType name="DateTimeOffset">  
      <xs:sequence minOccurs="1" maxOccurs="1">  
         <xs:element name="DateTime" type="xs:dateTime"  
         minOccurs="1" maxOccurs="1" />  
         <xs:elementname="OffsetMinutes" type="xs:short"  
         minOccurs="1" maxOccurs="1" />  
      </xs:sequence>  
   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf101-501">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf101-501">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 [<span data-ttu-id="bf101-502">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="bf101-502">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
