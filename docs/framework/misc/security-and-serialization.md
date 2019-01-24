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
ms.openlocfilehash: 996231ae035e6518aaceac0ba75b3de3b52a0a22
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640170"
---
# <a name="security-and-serialization"></a><span data-ttu-id="b3609-102">Zabezpečení a serializace</span><span class="sxs-lookup"><span data-stu-id="b3609-102">Security and Serialization</span></span>
<span data-ttu-id="b3609-103">Vzhledem k tomu, že serializace může povolit další kódu zobrazit nebo upravit data instance objektu, které by jinak bylo nedostupné, zvláštní oprávnění je požadováno pro kód, který provádí serializace: <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> příznak zadán.</span><span class="sxs-lookup"><span data-stu-id="b3609-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="b3609-104">Podle výchozích zásad Toto oprávnění nemá přístup k Internetu stáhnout nebo intranetu kód; Toto oprávnění je uděleno pouze kód v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="b3609-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="b3609-105">Za normálních okolností se serializují všechna pole instancí objektu, což znamená, že data jsou reprezentována v serializovaných datech pro instanci.</span><span class="sxs-lookup"><span data-stu-id="b3609-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="b3609-106">Je možné pro kód, který dokáže interpretovat formát, který určí, co data jsou hodnoty, nezávisle na usnadnění přístupu člena.</span><span class="sxs-lookup"><span data-stu-id="b3609-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="b3609-107">Deserializace podobně, extrahuje data ze serializované reprezentace a nastaví stav objektu přímo, znovu bez ohledu na pravidla přístupu.</span><span class="sxs-lookup"><span data-stu-id="b3609-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="b3609-108">Libovolný objekt, který by mohla obsahovat citlivá data by měla být neserializovatelný, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="b3609-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="b3609-109">Pokud musí být serializovatelný, zkuste provést konkrétní pole, které obsahují citlivá data neserializovatelné.</span><span class="sxs-lookup"><span data-stu-id="b3609-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="b3609-110">Pokud tuto akci nelze provést, mějte na paměti, že tato data vystavena jakýkoli kód, který má oprávnění k serializaci a ujistěte se, že žádný škodlivý kód dostat toto oprávnění.</span><span class="sxs-lookup"><span data-stu-id="b3609-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="b3609-111"><xref:System.Runtime.Serialization.ISerializable> Rozhraní je určena pro použití pouze v infrastruktuře serializace.</span><span class="sxs-lookup"><span data-stu-id="b3609-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="b3609-112">Ale pokud nechráněné, je potenciálně uvolnit citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="b3609-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="b3609-113">Pokud zadáte vlastní serializace prostřednictvím implementace **ISerializable**, ujistěte se, postupujte podle následujících opatření:</span><span class="sxs-lookup"><span data-stu-id="b3609-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
-   <span data-ttu-id="b3609-114"><xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Metody by měly být explicitně zabezpečeny buď vyhovovat i vašim náročným **SecurityPermission** s **SerializationFormatter** oprávnění zadaná nebo za zajištění, že žádné citlivé informace jsou vydány s výstupu metody.</span><span class="sxs-lookup"><span data-stu-id="b3609-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="b3609-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b3609-115">For example:</span></span>  
  
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
  
-   <span data-ttu-id="b3609-116">Speciální konstruktor použitý pro serializaci by měl také provést důkladné ověření vstupu a musí být chráněná nebo privátní k ochraně proti zneužití škodlivým kódem.</span><span class="sxs-lookup"><span data-stu-id="b3609-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="b3609-117">Ji by měl vynutit stejné kontroly zabezpečení a oprávnění nutná k získání instance této třídy jiným způsobem, jako je například vytvoření třídy explicitně nebo nepřímo vytváření prostřednictvím určitého druhu objektu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="b3609-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3609-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3609-118">See also</span></span>
- [<span data-ttu-id="b3609-119">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="b3609-119">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
