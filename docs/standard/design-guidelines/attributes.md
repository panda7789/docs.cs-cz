---
title: Atributy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: 3c0e1b8c20042c085d4ace996a084cbd464d3b21
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617558"
---
# <a name="attributes"></a>Atributy
<xref:System.Attribute?displayProperty=nameWithType>je základní třídou, která se používá k definování vlastních atributů.

 Atributy jsou poznámky, které lze přidat do programovacích prvků, jako jsou sestavení, typy, členy a parametry. Jsou uloženy v metadatech sestavení a lze k němu přistupovat za běhu pomocí rozhraní API pro reflexi. Rozhraní například definuje rozhraní <xref:System.ObsoleteAttribute> , které lze použít pro typ nebo člena k označení toho, že typ nebo člen je zastaralý.

 Atributy mohou mít jednu nebo více vlastností, které mohou obsahovat další data související s atributem. Například `ObsoleteAttribute` může obsahovat další informace o vydané verzi, ve které se typ nebo člen nepoužívá, a popis nových rozhraní API nahrazující zastaralé rozhraní API.

 Při použití atributu musí být zadány některé vlastnosti atributu. Jsou označovány jako požadované vlastnosti nebo požadované argumenty, protože jsou reprezentovány jako parametry pozičního konstruktoru. Například <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> vlastnost vlastnosti <xref:System.Diagnostics.ConditionalAttribute> je požadovaná vlastnost.

 Vlastnosti, které nemusí být nutně nutné zadat, když je atribut použit, se nazývají volitelné vlastnosti (nebo nepovinné argumenty). Jsou reprezentovány nastavitelnou vlastností. Kompilátory poskytují speciální syntaxi pro nastavení těchto vlastností při použití atributu. <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType>Vlastnost například představuje nepovinný argument.

 ✔️ vlastní třídy atributů Name s příponou "Attribute".

 ✔️ použít na <xref:System.AttributeUsageAttribute> vlastní atributy.

 ✔️ poskytují nastavitelné vlastnosti pro volitelné argumenty.

 ✔️ pro požadované argumenty Poskytněte vlastnosti jen pro získání.

 ✔️ poskytují parametry konstruktoru pro inicializaci vlastností, které odpovídají požadovaným argumentům. Každý parametr by měl mít stejný název (i v různých malých písmenech) jako odpovídající vlastnost.

 ❌Vyhněte se poskytování parametrů konstruktoru pro inicializaci vlastností odpovídajících volitelným argumentům.

 Jinými slovy, nemusíte mít vlastnosti, které lze nastavit pomocí konstruktoru i setter. Tyto zásady jsou velmi jasné, které argumenty jsou volitelné a které jsou povinné, a zabraňují se dvěma způsoby provádění stejných věcí.

 ❌Vyhněte se přetížení vlastních konstruktorů atributů.

 Existence pouze jednoho konstruktoru jasně komunikuje s uživatelem, který argumenty jsou povinné a které jsou volitelné.

 Pokud je to možné, ✔️ zapečetit vlastní třídy atributů. Díky tomu je hledání atributu rychlejší.

 *Částečně &copy; 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](index.md)
- [Pokyny k použití](usage-guidelines.md)
