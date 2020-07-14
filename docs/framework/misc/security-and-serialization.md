---
title: Zabezpečení a serializace
description: Přečtěte si o zabezpečení a serializaci. Pomocí SecurityPermission se zadaným příznakem SerializationFormatter můžete zobrazit nebo upravit data instance objektu.
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
ms.openlocfilehash: 79952ceee4c8b771aaadd4fc97a547bc65136770
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281261"
---
# <a name="security-and-serialization"></a><span data-ttu-id="08610-104">Zabezpečení a serializace</span><span class="sxs-lookup"><span data-stu-id="08610-104">Security and Serialization</span></span>
<span data-ttu-id="08610-105">Vzhledem k tomu, že serializace může ostatním kód dovolit zobrazit nebo upravit data instance objektů, která by jinak nebyla přístupná, je pro provádění serializace kódu vyžadováno speciální oprávnění: <xref:System.Security.Permissions.SecurityPermission> se <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> zadaným příznakem.</span><span class="sxs-lookup"><span data-stu-id="08610-105">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="08610-106">Podle výchozích zásad Toto oprávnění nemá přístup k Internetu stáhnout nebo intranetu kód; Toto oprávnění je uděleno pouze kód v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="08610-106">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="08610-107">Obvykle jsou všechna pole instance objektu serializována, což znamená, že data jsou reprezentována v serializovaných datech instance.</span><span class="sxs-lookup"><span data-stu-id="08610-107">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="08610-108">Je možné, že kód, který může interpretovat formát pro určení hodnot dat, nezávisle na přístupnost člena.</span><span class="sxs-lookup"><span data-stu-id="08610-108">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="08610-109">Podobně deserializace extrahuje data z serializované reprezentace a nastaví stav objektu přímo, a to bez ohledu na pravidla přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="08610-109">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="08610-110">Libovolný objekt, který by mohl obsahovat data citlivá na zabezpečení, by měl být, pokud je to možné, neserializovatelné.</span><span class="sxs-lookup"><span data-stu-id="08610-110">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="08610-111">Pokud musí být serializovatelný, zkuste nastavit konkrétní pole, která uchovávají citlivá data neserializovatelné.</span><span class="sxs-lookup"><span data-stu-id="08610-111">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="08610-112">Pokud to není možné, mějte na paměti, že tato data budou vystavena kódu, který má oprávnění k serializaci, a ujistěte se, že žádný škodlivý kód nemůže získat toto oprávnění.</span><span class="sxs-lookup"><span data-stu-id="08610-112">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="08610-113"><xref:System.Runtime.Serialization.ISerializable>Rozhraní je určeno pro použití pouze infrastrukturou serializace.</span><span class="sxs-lookup"><span data-stu-id="08610-113">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="08610-114">Pokud je ale nechráněný, může potenciálně vydávat citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="08610-114">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="08610-115">Pokud zadáte vlastní serializaci implementující rozhraní **ISerializable**, ujistěte se, že jste provedli následující opatření:</span><span class="sxs-lookup"><span data-stu-id="08610-115">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="08610-116"><xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>Metoda by měla být explicitně zabezpečena tím, že **SecurityPermission** vyžaduje, aby došlo k zadání **SerializationFormatter** oprávnění, nebo aby se zajistilo, že nejsou uvolněny žádné citlivé informace s výstupem metody.</span><span class="sxs-lookup"><span data-stu-id="08610-116">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="08610-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="08610-117">For example:</span></span>  
  
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
  
- <span data-ttu-id="08610-118">Speciální konstruktor, který se používá pro serializaci, by měl také provádět důkladné ověření vstupu a měl by být chráněný nebo soukromý, aby bylo možné chránit před zneužitím škodlivý kód.</span><span class="sxs-lookup"><span data-stu-id="08610-118">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="08610-119">Měla by vyhovět stejným kontrolám zabezpečení a oprávněním, která jsou nutná k získání instance této třídy jakýmkoli jiným způsobem, například explicitním vytvořením třídy nebo jejím přímým vytvořením pomocí nějakého typu objektu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="08610-119">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08610-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="08610-120">See also</span></span>

- [<span data-ttu-id="08610-121">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="08610-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
