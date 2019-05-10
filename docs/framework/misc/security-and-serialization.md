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
ms.openlocfilehash: c275e7179daf0dfdf2dda8bf364a4682565f28a6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596737"
---
# <a name="security-and-serialization"></a>Zabezpečení a serializace
Vzhledem k tomu, že serializace může povolit další kódu zobrazit nebo upravit data instance objektu, které by jinak bylo nedostupné, zvláštní oprávnění je požadováno pro kód, který provádí serializace: <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> příznak zadán. Podle výchozích zásad Toto oprávnění nemá přístup k Internetu stáhnout nebo intranetu kód; Toto oprávnění je uděleno pouze kód v místním počítači.  
  
 Za normálních okolností se serializují všechna pole instancí objektu, což znamená, že data jsou reprezentována v serializovaných datech pro instanci. Je možné pro kód, který dokáže interpretovat formát, který určí, co data jsou hodnoty, nezávisle na usnadnění přístupu člena. Deserializace podobně, extrahuje data ze serializované reprezentace a nastaví stav objektu přímo, znovu bez ohledu na pravidla přístupu.  
  
 Libovolný objekt, který by mohla obsahovat citlivá data by měla být neserializovatelný, pokud je to možné. Pokud musí být serializovatelný, zkuste provést konkrétní pole, které obsahují citlivá data neserializovatelné. Pokud tuto akci nelze provést, mějte na paměti, že tato data vystavena jakýkoli kód, který má oprávnění k serializaci a ujistěte se, že žádný škodlivý kód dostat toto oprávnění.  
  
 <xref:System.Runtime.Serialization.ISerializable> Rozhraní je určena pro použití pouze v infrastruktuře serializace. Ale pokud nechráněné, je potenciálně uvolnit citlivé informace. Pokud zadáte vlastní serializace prostřednictvím implementace **ISerializable**, ujistěte se, postupujte podle následujících opatření:  
  
- <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Metody by měly být explicitně zabezpečeny buď vyhovovat i vašim náročným **SecurityPermission** s **SerializationFormatter** oprávnění zadaná nebo za zajištění, že žádné citlivé informace jsou vydány s výstupu metody. Příklad:  
  
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
  
- Speciální konstruktor použitý pro serializaci by měl také provést důkladné ověření vstupu a musí být chráněná nebo privátní k ochraně proti zneužití škodlivým kódem. Ji by měl vynutit stejné kontroly zabezpečení a oprávnění nutná k získání instance této třídy jiným způsobem, jako je například vytvoření třídy explicitně nebo nepřímo vytváření prostřednictvím určitého druhu objektu pro vytváření.  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
