---
title: Prázdné znaky a mezer významné zpracování při načítání modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8e2279023029b5047cc7d9b4d0d97ac1f21e3f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569067"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Prázdné znaky a mezer významné zpracování při načítání modelu DOM
Při načítání dokumentu, můžete nastavit možnost zachování mezer a vytvořit **XmlWhitespace** uzly ve stromu dokumentu. Chcete-li vytvořit mezer uzly, nastavte **PreserveWhitespace** vlastnost na hodnotu true. Pokud je nastavena na **false**, který je výchozí, nejsou vytvořeny uzly mezer. Uzly významné prázdné znaky se vždycky zachovají, a **XmlSignificantWhitespace** uzly jsou vždy vytvořené v paměti představují tato data, bez ohledu na to, že v nastavení **PreserveWhitespace** příznak.  
  
 Pokud dokument je načtena z čtečka čipových karet, potom nastavení z **PreserveWhitespace** příznak vlastnost na **třídou XMLDocument nastavenou na** třída má vliv na vytváření **XmlWhitespace** uzly pouze tehdy, když **WhitespaceHandling** vlastnost **XmlTextReader** není nastavený na **: WhitespaceHandling.None**. Je hodnota **WhitespaceHandling** vlastnost čtecímu modulu, který má přednost před nastavením tohoto příznaku na **třídou XMLDocument nastavenou na**. Další informace o **XmlSignificantWhitespace**, najdete v části <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
