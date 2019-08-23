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
ms.openlocfilehash: a5aebac2d392d4540581dfe7c7afff0819968ac0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912545"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="3d1d2-102">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="3d1d2-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="3d1d2-103">Digitální podpisy zajišťují, že při posílání z jednoho programu do druhého se data neúmyslně nezměnila.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="3d1d2-104">Digitální podpis se obvykle počítá použitím matematické funkce na hodnotu hash dat, která mají být podepsána.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="3d1d2-105">Při formátování hodnoty hash, která má být podepsána, některé algoritmy digitálního podpisu připojí jako součást operace formátování identifikátor objektu ASN. 1 (OID).</span><span class="sxs-lookup"><span data-stu-id="3d1d2-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="3d1d2-106">Identifikátor OID identifikuje algoritmus, který se použil k výpočtu hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="3d1d2-107">Můžete mapovat algoritmy na identifikátory objektů a roztáhnout mechanismus kryptografie na použití vlastních algoritmů.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="3d1d2-108">Následující příklad ukazuje, jak namapovat identifikátor objektu na nový algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="3d1d2-109">Element oidEntry > obsahuje dva atributy. [ \<](./file-schema/cryptography/oidentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="3d1d2-109">The [\<oidEntry> element](./file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="3d1d2-110">Atribut **OID** je číslo identifikátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="3d1d2-111">Atribut **Name** je hodnota [ \<](./file-schema/cryptography/nameentry-element.md)atributu **Name** z > elementu nameEntry.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="3d1d2-112">Aby bylo možné mapovat identifikátor objektu na jednoduchý název, musí být mapování z názvu algoritmu na třídu.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d1d2-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d1d2-113">See also</span></span>

- [<span data-ttu-id="3d1d2-114">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="3d1d2-114">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
- [<span data-ttu-id="3d1d2-115">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="3d1d2-115">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
