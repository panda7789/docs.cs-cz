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
ms.openlocfilehash: e0b1f8979929dbb6872bbd53e1840b2d0520a31d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910674"
---
# <a name="security-and-serialization"></a><span data-ttu-id="79d57-102">Zabezpečení a serializace</span><span class="sxs-lookup"><span data-stu-id="79d57-102">Security and Serialization</span></span>
<span data-ttu-id="79d57-103">Vzhledem k tomu, že serializace může ostatním kód dovolit zobrazit nebo upravit data instance objektů, která by jinak nebyla přístupná, je pro provádění serializace <xref:System.Security.Permissions.SecurityPermission> kódu vyžadováno <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> speciální oprávnění: se zadaným příznakem.</span><span class="sxs-lookup"><span data-stu-id="79d57-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="79d57-104">Podle výchozích zásad Toto oprávnění nemá přístup k Internetu stáhnout nebo intranetu kód; Toto oprávnění je uděleno pouze kód v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="79d57-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="79d57-105">Obvykle jsou všechna pole instance objektu serializována, což znamená, že data jsou reprezentována v serializovaných datech instance.</span><span class="sxs-lookup"><span data-stu-id="79d57-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="79d57-106">Je možné, že kód, který může interpretovat formát pro určení hodnot dat, nezávisle na přístupnost člena.</span><span class="sxs-lookup"><span data-stu-id="79d57-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="79d57-107">Podobně deserializace extrahuje data z serializované reprezentace a nastaví stav objektu přímo, a to bez ohledu na pravidla přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="79d57-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="79d57-108">Libovolný objekt, který by mohl obsahovat data citlivá na zabezpečení, by měl být, pokud je to možné, neserializovatelné.</span><span class="sxs-lookup"><span data-stu-id="79d57-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="79d57-109">Pokud musí být serializovatelný, zkuste nastavit konkrétní pole, která uchovávají citlivá data neserializovatelné.</span><span class="sxs-lookup"><span data-stu-id="79d57-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="79d57-110">Pokud to není možné, mějte na paměti, že tato data budou vystavena kódu, který má oprávnění k serializaci, a ujistěte se, že žádný škodlivý kód nemůže získat toto oprávnění.</span><span class="sxs-lookup"><span data-stu-id="79d57-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="79d57-111"><xref:System.Runtime.Serialization.ISerializable> Rozhraní je určeno pro použití pouze infrastrukturou serializace.</span><span class="sxs-lookup"><span data-stu-id="79d57-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="79d57-112">Pokud je ale nechráněný, může potenciálně vydávat citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="79d57-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="79d57-113">Pokud zadáte vlastní serializaci implementující rozhraní **ISerializable**, ujistěte se, že jste provedli následující opatření:</span><span class="sxs-lookup"><span data-stu-id="79d57-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="79d57-114">Metoda by měla být explicitně zabezpečena tím, že vyžaduje, aby došlo k zadání **SerializationFormatter** oprávnění, nebo aby se zajistilo, že nejsou uvolněny žádné citlivé informace s výstupem metody. <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A></span><span class="sxs-lookup"><span data-stu-id="79d57-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="79d57-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="79d57-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="79d57-116">Speciální konstruktor, který se používá pro serializaci, by měl také provádět důkladné ověření vstupu a měl by být chráněný nebo soukromý, aby bylo možné chránit před zneužitím škodlivý kód.</span><span class="sxs-lookup"><span data-stu-id="79d57-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="79d57-117">Měla by vyhovět stejným kontrolám zabezpečení a oprávněním, která jsou nutná k získání instance této třídy jakýmkoli jiným způsobem, například explicitním vytvořením třídy nebo jejím přímým vytvořením pomocí nějakého typu objektu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="79d57-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79d57-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79d57-118">See also</span></span>

- [<span data-ttu-id="79d57-119">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="79d57-119">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
