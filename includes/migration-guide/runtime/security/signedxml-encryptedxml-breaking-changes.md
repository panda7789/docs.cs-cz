---
ms.openlocfilehash: 8cc4f2ba2923774ef4e4e6861a89a7797ca988e1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621079"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a>SignedXml a EncryptedXml – průlomové změny

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.6.2 opravy zabezpečení v nástroji <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> a <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> vedou k různým chování za běhu. Třeba<ul><li>Pokud má dokument více elementů se stejným <code>id</code> atributem a signatura cílí na jeden z těchto prvků jako kořen podpisu, dokument bude nyní považován za neplatný.</li><li>Dokumenty, které používají nekanonické transformační algoritmy XPath v odkazech, jsou nyní považovány za neplatné.</li><li>Dokumenty, které používají nekanonické transformační algoritmy XSLT v odkazech, nyní považují za neplatné.</li><li>Žádný program, který používá odpojené podpisy externích prostředků, to nebude moci udělat.</li></ul>

#### <a name="suggestion"></a>Návrh

Vývojáři mohou chtít zkontrolovat použití <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> a a <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> také typy odvozené od <xref:System.Security.Cryptography.Xml.Transform> příjemce dokumentu nemusí být schopni je zpracovat.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6.2|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
