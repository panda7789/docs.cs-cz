---
title: Mapování identifikátorů objektů na algoritmy šifrování
description: Podívejte se, jak namapovat identifikátor objektu (OID) na kryptografický algoritmus v rozhraní .NET pomocí prvků oidEntry a nameEntry v konfiguračním souboru XML.
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: e22510014071455b83ba28cd82690b5ecdce9bc9
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2020
ms.locfileid: "85142001"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="354bb-103">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="354bb-103">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="354bb-104">Digitální podpisy zajišťují, že při posílání z jednoho programu do druhého se data neúmyslně nezměnila.</span><span class="sxs-lookup"><span data-stu-id="354bb-104">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="354bb-105">Digitální podpis se obvykle počítá použitím matematické funkce na hodnotu hash dat, která mají být podepsána.</span><span class="sxs-lookup"><span data-stu-id="354bb-105">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="354bb-106">Při formátování hodnoty hash, která má být podepsána, některé algoritmy digitálního podpisu připojí jako součást operace formátování identifikátor objektu ASN. 1 (OID).</span><span class="sxs-lookup"><span data-stu-id="354bb-106">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="354bb-107">Identifikátor OID identifikuje algoritmus, který se použil k výpočtu hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="354bb-107">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="354bb-108">Můžete mapovat algoritmy na identifikátory objektů a roztáhnout mechanismus kryptografie na použití vlastních algoritmů.</span><span class="sxs-lookup"><span data-stu-id="354bb-108">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="354bb-109">Následující příklad ukazuje, jak namapovat identifikátor objektu na nový algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="354bb-109">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="354bb-110">[ \<oidEntry> Element](./file-schema/cryptography/oidentry-element.md) obsahuje dva atributy.</span><span class="sxs-lookup"><span data-stu-id="354bb-110">The [\<oidEntry> element](./file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="354bb-111">Atribut **OID** je číslo identifikátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="354bb-111">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="354bb-112">Atribut **Name** je hodnota atributu **Name** z [ \<nameEntry> elementu](./file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="354bb-112">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="354bb-113">Aby bylo možné mapovat identifikátor objektu na jednoduchý název, musí být mapování z názvu algoritmu na třídu.</span><span class="sxs-lookup"><span data-stu-id="354bb-113">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="354bb-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="354bb-114">See also</span></span>

- [<span data-ttu-id="354bb-115">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="354bb-115">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
- [<span data-ttu-id="354bb-116">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="354bb-116">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
