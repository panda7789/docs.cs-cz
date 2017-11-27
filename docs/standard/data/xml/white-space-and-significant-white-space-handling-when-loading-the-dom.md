---
title: "Prázdné znaky a mezer významné zpracování při načítání modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 82401a18132801f9aa5368832b96be3cb67a8642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Prázdné znaky a mezer významné zpracování při načítání modelu DOM
Při načítání dokumentu, můžete nastavit možnost zachování mezer a vytvořit **XmlWhitespace** uzly ve stromu dokumentu. Chcete-li vytvořit mezer uzly, nastavte **PreserveWhitespace** vlastnost na hodnotu true. Pokud je nastavena na **false**, který je výchozí, nejsou vytvořeny uzly mezer. Uzly významné prázdné znaky se vždycky zachovají, a **XmlSignificantWhitespace** uzly jsou vždy vytvořené v paměti představují tato data, bez ohledu na to, že v nastavení **PreserveWhitespace** příznak.  
  
 Pokud dokument je načtena z čtečka čipových karet, potom nastavení z **PreserveWhitespace** příznak vlastnost na **třídou XMLDocument nastavenou na** třída má vliv na vytváření **XmlWhitespace** uzly pouze tehdy, když **WhitespaceHandling** vlastnost **XmlTextReader** není nastavený na **: WhitespaceHandling.None**. Je hodnota **WhitespaceHandling** vlastnost čtecímu modulu, který má přednost před nastavením tohoto příznaku na **třídou XMLDocument nastavenou na**. Další informace o **XmlSignificantWhitespace**, najdete v části <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>Viz také  
 [XML Document Object Model (DOM).](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
