---
title: Zabezpečení a serializace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a30e80b1b4a412405787c0c14ad58995a2d7fffc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394245"
---
# <a name="security-and-serialization"></a><span data-ttu-id="0422c-102">Zabezpečení a serializace</span><span class="sxs-lookup"><span data-stu-id="0422c-102">Security and Serialization</span></span>
<span data-ttu-id="0422c-103">Protože serializace můžete povolit jiný kód, zobrazit nebo upravit data instance objektů, které by jinak nedostupná, speciální oprávnění jsou nutná kódu provádění serializace: <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> příznak.</span><span class="sxs-lookup"><span data-stu-id="0422c-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="0422c-104">Podle výchozích zásad Toto oprávnění nemá přístup k Internetu stáhnout nebo intranetu kód; Toto oprávnění je uděleno pouze kód v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="0422c-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="0422c-105">Za normálních okolností se serializují všechna pole instance objektu, což znamená, že data jsou reprezentována v serializovaných datech pro instanci.</span><span class="sxs-lookup"><span data-stu-id="0422c-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="0422c-106">Je možné pro kód, který dokáže interpretovat formát, který se zjistit, co jsou hodnoty dat, nezávisle na přístupnosti člena.</span><span class="sxs-lookup"><span data-stu-id="0422c-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="0422c-107">Podobně deserializace extrahuje data ze serializované reprezentace a nastaví stav objektu přímo, znovu bez ohledu na pravidla přístupu.</span><span class="sxs-lookup"><span data-stu-id="0422c-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="0422c-108">Libovolný objekt, který může obsahovat data citlivým z hlediska zabezpečení by měl být neserializovatelný, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="0422c-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="0422c-109">Pokud musí být serializovatelný, zkuste provést konkrétní pole, které obsahují citlivá data neserializovatelné.</span><span class="sxs-lookup"><span data-stu-id="0422c-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="0422c-110">Pokud tuto změnu nelze provést, mějte na paměti, že tato data budou vystavena kód, který má oprávnění k serializaci a ujistěte se, že žádný škodlivý kód můžete získat toto oprávnění.</span><span class="sxs-lookup"><span data-stu-id="0422c-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="0422c-111"><xref:System.Runtime.Serialization.ISerializable> Rozhraní je určena pro použití pouze infrastrukturou serializace.</span><span class="sxs-lookup"><span data-stu-id="0422c-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="0422c-112">Ale pokud nechráněné, je potenciálně uvolnit citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="0422c-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="0422c-113">Pokud jste zadali vlastní serializace implementací **ISerializable**, ujistěte se, postupujte podle následujících opatření:</span><span class="sxs-lookup"><span data-stu-id="0422c-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
-   <span data-ttu-id="0422c-114"><xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Metoda by měla být explicitně zabezpečena požadavkem **SecurityPermission** s **SerializationFormatter** oprávnění zadaný nebo nástrojem a ověřte, zda žádná velká a malá písmena informace o vydání pomocí výstupu metody.</span><span class="sxs-lookup"><span data-stu-id="0422c-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="0422c-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0422c-115">For example:</span></span>  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter   
    =true)]  
    public override void GetObjectData(SerializationInfo info,   
    StreamingContext context)  
    {  
    }  
    ```  
  
-   <span data-ttu-id="0422c-116">Zvláštní konstruktor pro serializaci by také provést důkladné ověřování vstupu a musí být chráněný nebo privátní zajistit ochranu proti zneužití škodlivý kód.</span><span class="sxs-lookup"><span data-stu-id="0422c-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="0422c-117">Měla vynutit, stejné kontroly zabezpečení a oprávnění potřebná k získání instance této třídy jiným způsobem, jako je například explicitně vytvořením třídy nebo nepřímo přes určitého druhu objektu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="0422c-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0422c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="0422c-118">See Also</span></span>  
 [<span data-ttu-id="0422c-119">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="0422c-119">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
