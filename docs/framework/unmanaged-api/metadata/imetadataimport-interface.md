---
title: IMetaDataImport – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport
helpviewer_keywords:
- IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0adbbd35-5e8d-4fec-8268-dc70a07c5975
topic_type:
- apiref
ms.openlocfilehash: 2d45a369def193b9c8d8f9a3aa954ede600a87dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434734"
---
# <a name="imetadataimport-interface"></a>IMetaDataImport – rozhraní
Provides methods for importing and manipulating existing metadata from a portable executable (PE) file or other source, such as a type library or a stand-alone, run-time metadata binary.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CloseEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Closes the enumerator with the specified handle.|  
|[CountEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Gets the number of elements in the enumerator with the specified handle.|  
|[EnumCustomAttributes – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Enumerates a list of custom attribute-definition tokens associated with the specified type or member.|  
|[EnumEvents – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Enumerates event definition tokens for the specified TypeDef token.|  
|[EnumFields – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.|  
|[EnumFieldsWithName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Enumerates FieldDef tokens of the specified type with the specified name.|  
|[EnumInterfaceImpls – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Enumerates MethodDef tokens representing interface implementations.|  
|[EnumMemberRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Enumerates MemberRef tokens representing members of the specified type.|  
|[EnumMembers – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Enumerates MemberDef tokens representing members of the specified type.|  
|[EnumMembersWithName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Enumerates MemberDef tokens representing members of the specified type with the specified name.|  
|[EnumMethodImpls – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.|  
|[EnumMethods – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Enumerates MethodDef tokens representing methods of the specified type.|  
|[EnumMethodSemantics – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Enumerates the properties and the property-change events to which the specified method is related.|  
|[EnumMethodsWithName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.|  
|[EnumModuleRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|Enumerates ModuleRef tokens that represent imported modules.|  
|[EnumParams – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.|  
|[EnumPermissionSets – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Enumerates permissions for the objects in a specified metadata scope.|  
|[EnumProperties – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.|  
|[EnumSignatures – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Enumerates Signature tokens representing stand-alone signatures in the current scope.|  
|[EnumTypeDefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Enumerates TypeDef tokens representing all types within the current scope.|  
|[EnumTypeRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Enumerates TypeRef tokens defined in the current metadata scope.|  
|[EnumTypeSpecs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Enumerates TypeSpec tokens defined in the current metadata scope.|  
|[EnumUnresolvedMethods – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.|  
|[EnumUserStrings – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Enumerates String tokens representing hard-coded strings in the current metadata scope.|  
|[FindField – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|Gets the FieldDef token for the field that is a member of the specified type, and has the specified name and metadata signature.|  
|[FindMember – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Gets a pointer to the MemberDef token for the member defined by the specified type with the specified name and metadata signature.|  
|[FindMemberRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Gets a pointer to the MemberRef token for the member defined by the specified type with the specified name and metadata signature.|  
|[FindMethod – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Gets a pointer to the MethodDef token for the method defined by the specified type with the specified name and metadata signature.|  
|[FindTypeDefByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Gets a pointer to the TypeDef metadata token for the type with the specified name.|  
|[FindTypeRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Gets a pointer to the TypeRef metadata token that references the type in the specified search scope with the specified name.|  
|[GetClassLayout – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Gets layout information for the class referenced by the specified TypeDef token.|  
|[GetCustomAttributeByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Gets the value of the custom attribute, given its name.|  
|[GetCustomAttributeProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Gets the value of the custom attribute, given its metadata token.|  
|[GetEventProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Gets metadata information (including the declaring type, the add and remove methods for delegates, and any flags and other associated data) for the event represented by the specified event token.|  
|[GetFieldMarshal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Gets a pointer to the native, unmanaged type of the field represented by the specified Field metadata token.|  
|[GetFieldProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Gets metadata associated with the field referenced by the specified FieldDef token.|  
|[GetInterfaceImplProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Gets a pointer to the metadata tokens for the type that implements the specified method and for the interface that declares that method.|  
|[GetMemberProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Gets metadata information (including the name, binary signature, and relative virtual address) of the type member referenced by the specified metadata token.|  
|[GetMemberRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Gets metadata associated with the member referenced by the specified token.|  
|[GetMethodProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Gets the metadata associated with the method referenced by the specified MethodDef token.|  
|[GetMethodSemantics – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Gets a pointer to the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.|  
|[GetModuleFromScope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Gets a pointer to the metadata token for the module referenced in the current metadata scope.|  
|[GetModuleRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Gets the name of the module referenced by the specified metadata token.|  
|[GetNameFromToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Gets the UTF-8 name of the object referenced by the specified metadata token.|  
|[GetNativeCallConvFromSig – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Gets the native calling convention for the method that is represented by the specified signature pointer.|  
|[GetNestedClassProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|Gets the TypeDef token for the enclosing parent type of the specified nested type.|  
|[GetParamForMethodIndex – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Gets a pointer to the token that represents the parameter at the specified ordinal position in the sequence of method parameters for the method represented by the specified MethodDef token.|  
|[GetParamProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Gets metadata values for the parameter referenced by the specified ParamDef token.|  
|[GetPermissionSetProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Gets the metadata associated with the System.Security.PermissionSet represented by the specified Permission token.|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Gets a ModuleRef token to represent the target assembly of a PInvoke call.|  
|[GetPropertyProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Gets the metadata associated with the property represented by the specified token.|  
|[GetRVA – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Gets the offset of the relative virtual address of the code object represented by the specified token.|  
|[GetScopeProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.|  
|[GetSigFromToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Gets the binary metadata signature associated with the specified token.|  
|[GetTypeDefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Returns metadata information for the type represented by the specified TypeDef token.|  
|[GetTypeRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Gets the metadata associated with the type referenced by the specified TypeRef token.|  
|[GetTypeSpecFromToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Gets the binary metadata signature of the type specification represented by the specified token.|  
|[GetUserString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Gets the literal string represented by the specified metadata token.|  
|[IsGlobal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.|  
|[IsValidToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Gets a value indicating whether the specified token holds a valid reference to a code object.|  
|[ResetEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Resets the specified enumerator to the specified position.|  
|[ResolveTypeRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Gets type information for the type referenced by the specified TypeRef token.|  
  
## <a name="remarks"></a>Poznámky  
 The design of the `IMetaDataImport` interface is intended primarily to be used by tools and services that will be importing type information (for example, development tools) or managing deployed components (for example, resolution/activation services). The methods in `IMetaDataImport` fall into the following task categories:  
  
- Enumerating collections of items in the metadata scope.  
  
- Finding an item that has a specific set of characteristics.  
  
- Getting properties of a specified item.  
  
- The Get methods are specifically designed to return single-valued properties of a metadata item. When the property is a reference to another item, a token for that item is returned. Any pointer input type can be NULL to indicate that the particular value is not being requested. To obtain properties that are essentially collection objects (for example, the collection of interfaces that a class implements), use the enumeration methods.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
