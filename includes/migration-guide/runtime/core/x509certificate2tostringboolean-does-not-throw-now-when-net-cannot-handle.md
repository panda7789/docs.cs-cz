---
ms.openlocfilehash: d48519443aeee05617538cf2cc12bea49ad3e16d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858584"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2.ToString(Boolean) nevyvolá nyní při .NET nemůže zpracovat certifikát

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5.2 a dřívějších verzích, tato metoda vyvolá-li <code>true</code> byla předána parametru verbose nebyly nainstalovány certifikáty, které nejsou podporované rozhraním .NET Framework. Metoda teď bude úspěšné a vrátit platný řetězec, který vynechá části nepřístupný certifikátu.|
|Doporučení|Žádný kód v závislosti na <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> očekávat, že vrácený řetězec může vyloučit některé data certifikátu (jako je například veřejný klíč, privátní klíč a rozšíření) v některých případech, ve kterých rozhraní API by mít dříve vyvolána je třeba aktualizovat.|
|Scope|Edge|
|Version|4.6|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|

