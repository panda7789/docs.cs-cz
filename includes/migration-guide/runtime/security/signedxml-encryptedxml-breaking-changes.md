---
ms.openlocfilehash: 68da7216890da1819a994161507355a0b5ea1f9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857567"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a>Změny rozdělení signedxml a encryptedxml

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 zabezpečení opravuje <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=name> a <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=name> vést k různým chováním za běhu. Například:<ul><li>Pokud dokument obsahuje více prvků <code>id</code> se stejným atributem a podpis cílí na jeden z těchto prvků jako kořen podpisu, bude dokument nyní považován za neplatný.</li><li>Dokumenty používající nekanonické algoritmy transformace XPath v odkazech jsou nyní považovány za neplatné.</li><li>Dokumenty používající nekanonické algoritmy transformace XSLT v odkazech jsou nyní neplatné.</li><li>Žádný program využívající podpisy odpojené externí prostředky nebude moci tak učinit.</li></ul>|
|Návrh|Vývojáři mohou chtít zkontrolovat <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>použití a , stejně <xref:System.Security.Cryptography.Xml.Transform> jako typy odvozené od protože příjemce dokumentu nemusí být schopen zpracovat.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
