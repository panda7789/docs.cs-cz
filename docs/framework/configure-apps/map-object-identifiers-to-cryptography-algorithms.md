---
title: Mapování identifikátorů objektů na algoritmy šifrování
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7801c55cf6b3334347788013d9052038d5d2f3ec
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756615"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="d0815-102">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="d0815-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="d0815-103">Digitální podpisy Ujistěte se, že data není manipulováno při odeslání z jedné aplikace do jiného.</span><span class="sxs-lookup"><span data-stu-id="d0815-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="d0815-104">Digitální podpis je obvykle počítaný použitím matematické funkce hash data, která mají být podepsané.</span><span class="sxs-lookup"><span data-stu-id="d0815-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="d0815-105">Při formátování hodnotu hash podepsat, některé algoritmy digitální podpis připojí ASN.1 identifikátor objektu (OID) v rámci operace formátování.</span><span class="sxs-lookup"><span data-stu-id="d0815-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="d0815-106">Identifikátor OID Určuje algoritmus, který se používá k výpočtu hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="d0815-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="d0815-107">Identifikátory objektů rozšířit mechanismus na kryptografické algoritmy vlastní můžete namapovat algoritmy.</span><span class="sxs-lookup"><span data-stu-id="d0815-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="d0815-108">Následující příklad ukazuje, jak k mapování identifikátor objektu na nový algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="d0815-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="d0815-109">[ \<Oidentry – > element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) obsahuje dva atributy.</span><span class="sxs-lookup"><span data-stu-id="d0815-109">The [\<oidEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="d0815-110">**OID** atribut je identifikátor objektu.</span><span class="sxs-lookup"><span data-stu-id="d0815-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="d0815-111">**Název** atribut je hodnota **název** atribut z [ \<nameEntry > element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="d0815-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="d0815-112">Musí existovat mapování z název algoritmu na třídu před identifikátor objektu lze mapovat na jednoduchý název.</span><span class="sxs-lookup"><span data-stu-id="d0815-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0815-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0815-113">See Also</span></span>  
 [<span data-ttu-id="d0815-114">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="d0815-114">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="d0815-115">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="d0815-115">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
