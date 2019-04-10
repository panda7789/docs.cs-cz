---
ms.openlocfilehash: 68da7216890da1819a994161507355a0b5ea1f9f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236014"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a>SignedXml a EncryptedXml Rozbíjející změny v

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2, opravy zabezpečení v <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=name> a <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=name> může vést k jiné chování za běhu. Například<ul><li>Pokud dokument má více elementů se stejnou <code>id</code> atribut a podpis cílí na jeden z těchto elementů jako kořenový podpis, dokument se nyní být považované za neplatné.</li><li>Dokumenty pomocí jiné kanonické algoritmy transformace XPath v odkazech jsou nyní považovány za neplatné.</li><li>Dokumenty pomocí jiné kanonické algoritmy transformace XSLT v odkazech se teď se podíváme neplatný.</li><li>Provedete to tak nebude možné jakékoli program využívající podpisy externí prostředek odpojit.</li></ul>|
|Doporučení|Vývojáři chtít Zkontrolujte použití <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> a <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, stejně jako typy odvozené z <xref:System.Security.Cryptography.Xml.Transform> od dokumentu příjemce nemusí být možné zpracovat.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
