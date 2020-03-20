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
ms.openlocfilehash: 634388e3920e0b9dbee85aa3ea555471cee604ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181119"
---
# <a name="security-and-serialization"></a><span data-ttu-id="2d53e-102">Zabezpečení a serializace</span><span class="sxs-lookup"><span data-stu-id="2d53e-102">Security and Serialization</span></span>
<span data-ttu-id="2d53e-103">Vzhledem k tomu, že serializace může umožnit jinému kódu zobrazit nebo upravit data instance <xref:System.Security.Permissions.SecurityPermission> objektu, která by jinak byla nepřístupná, je vyžadováno zvláštní oprávnění kódu provádějícímserializaci: se zadaným příznakem. <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter></span><span class="sxs-lookup"><span data-stu-id="2d53e-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="2d53e-104">Podle výchozích zásad Toto oprávnění nemá přístup k Internetu stáhnout nebo intranetu kód; Toto oprávnění je uděleno pouze kód v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="2d53e-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="2d53e-105">Za normálních okolností jsou všechna pole instance objektu serializována, což znamená, že data jsou reprezentována v serializovaných datech pro instanci.</span><span class="sxs-lookup"><span data-stu-id="2d53e-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="2d53e-106">Je možné pro kód, který může interpretovat formát k určení, jaké jsou hodnoty dat, nezávisle na usnadnění přístupu člena.</span><span class="sxs-lookup"><span data-stu-id="2d53e-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="2d53e-107">Podobně deserializace extrahuje data z serializované reprezentace a nastaví stav objektu přímo, opět bez ohledu na pravidla usnadnění.</span><span class="sxs-lookup"><span data-stu-id="2d53e-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="2d53e-108">Jakýkoli objekt, který by mohl obsahovat data citlivá na zabezpečení, by měl být pokud možno neserializovatelný.</span><span class="sxs-lookup"><span data-stu-id="2d53e-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="2d53e-109">Pokud musí být serializovatelný, pokuste se, aby určitá pole, která obsahuje citlivá data neserializovatelné.</span><span class="sxs-lookup"><span data-stu-id="2d53e-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="2d53e-110">Pokud to nelze provést, uvědomte si, že tato data budou vystavena jakémukoli kódu, který má oprávnění k serializaci, a ujistěte se, že žádné škodlivé kódy mohou získat toto oprávnění.</span><span class="sxs-lookup"><span data-stu-id="2d53e-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="2d53e-111">Rozhraní <xref:System.Runtime.Serialization.ISerializable> je určeno pouze pro infrastrukturu serializace.</span><span class="sxs-lookup"><span data-stu-id="2d53e-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="2d53e-112">Však pokud není chráněn, může potenciálně uvolnit citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="2d53e-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="2d53e-113">Pokud zadáte vlastní serializaci implementací **ISerializable**, ujistěte se, že provést následující opatření:</span><span class="sxs-lookup"><span data-stu-id="2d53e-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="2d53e-114">Metoda <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> by měla být explicitně zabezpečena buď požadavkem **SecurityPermission** s **SerializationFormatter** oprávnění zadané nebo ujistěte se, že žádné citlivé informace je uvolněna s výstupem metody.</span><span class="sxs-lookup"><span data-stu-id="2d53e-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="2d53e-115">Například:</span><span class="sxs-lookup"><span data-stu-id="2d53e-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="2d53e-116">Speciální konstruktor používaný pro serializaci by měl také provádět důkladné ověření vstupu a měl by být chráněn nebo soukromý, aby pomohl chránit před zneužitím škodlivým kódem.</span><span class="sxs-lookup"><span data-stu-id="2d53e-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="2d53e-117">Měl by vynutit stejné kontroly zabezpečení a oprávnění potřebné k získání instance takové třídy jinými prostředky, jako je například explicitní vytvoření třídy nebo nepřímé vytvoření prostřednictvím nějakého druhu továrny.</span><span class="sxs-lookup"><span data-stu-id="2d53e-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d53e-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d53e-118">See also</span></span>

- [<span data-ttu-id="2d53e-119">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="2d53e-119">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
