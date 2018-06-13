---
title: Kolekcemi schémat OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: f1cb5e1fe967088b44fa4045dfe50c1c57d963eb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766930"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="d8468-102">Kolekcemi schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="d8468-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="d8468-103">Tato část popisuje podporu kolekci schématu pro zprostředkovatele OLE DB pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="d8468-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="d8468-104">Zprostředkovatel Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="d8468-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="d8468-105">Microsoft SQL Server OLE DB ovladač podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="d8468-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="d8468-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="d8468-106">Tables</span></span>  
  
-   <span data-ttu-id="d8468-107">Sloupce</span><span class="sxs-lookup"><span data-stu-id="d8468-107">Columns</span></span>  
  
-   <span data-ttu-id="d8468-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="d8468-108">Procedures</span></span>  
  
-   <span data-ttu-id="d8468-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d8468-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="d8468-110">Katalogu</span><span class="sxs-lookup"><span data-stu-id="d8468-110">Catalog</span></span>  
  
-   <span data-ttu-id="d8468-111">Indexy</span><span class="sxs-lookup"><span data-stu-id="d8468-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="d8468-112">Tabulky</span><span class="sxs-lookup"><span data-stu-id="d8468-112">Tables</span></span>  
  
|<span data-ttu-id="d8468-113">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-113">ColumnName</span></span>|<span data-ttu-id="d8468-114">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-115">TABLE_CATALOG</span></span>|<span data-ttu-id="d8468-116">String</span><span class="sxs-lookup"><span data-stu-id="d8468-116">String</span></span>|  
|<span data-ttu-id="d8468-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8468-118">String</span><span class="sxs-lookup"><span data-stu-id="d8468-118">String</span></span>|  
|<span data-ttu-id="d8468-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-119">TABLE_NAME</span></span>|<span data-ttu-id="d8468-120">String</span><span class="sxs-lookup"><span data-stu-id="d8468-120">String</span></span>|  
|<span data-ttu-id="d8468-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8468-121">TABLE_TYPE</span></span>|<span data-ttu-id="d8468-122">String</span><span class="sxs-lookup"><span data-stu-id="d8468-122">String</span></span>|  
|<span data-ttu-id="d8468-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-123">TABLE_GUID</span></span>|<span data-ttu-id="d8468-124">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-124">Guid</span></span>|  
|<span data-ttu-id="d8468-125">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-125">DESCRIPTION</span></span>|<span data-ttu-id="d8468-126">String</span><span class="sxs-lookup"><span data-stu-id="d8468-126">String</span></span>|  
|<span data-ttu-id="d8468-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="d8468-127">TABLE_PROPID</span></span>|<span data-ttu-id="d8468-128">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-128">Int64</span></span>|  
|<span data-ttu-id="d8468-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d8468-129">DATE_CREATED</span></span>|<span data-ttu-id="d8468-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-130">DateTime</span></span>|  
|<span data-ttu-id="d8468-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d8468-131">DATE_MODIFIED</span></span>|<span data-ttu-id="d8468-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d8468-133">Sloupce</span><span class="sxs-lookup"><span data-stu-id="d8468-133">Columns</span></span>  
  
|<span data-ttu-id="d8468-134">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-134">ColumnName</span></span>|<span data-ttu-id="d8468-135">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-136">TABLE_CATALOG</span></span>|<span data-ttu-id="d8468-137">String</span><span class="sxs-lookup"><span data-stu-id="d8468-137">String</span></span>|  
|<span data-ttu-id="d8468-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8468-139">String</span><span class="sxs-lookup"><span data-stu-id="d8468-139">String</span></span>|  
|<span data-ttu-id="d8468-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-140">TABLE_NAME</span></span>|<span data-ttu-id="d8468-141">String</span><span class="sxs-lookup"><span data-stu-id="d8468-141">String</span></span>|  
|<span data-ttu-id="d8468-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-142">COLUMN_NAME</span></span>|<span data-ttu-id="d8468-143">String</span><span class="sxs-lookup"><span data-stu-id="d8468-143">String</span></span>|  
|<span data-ttu-id="d8468-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-144">COLUMN_GUID</span></span>|<span data-ttu-id="d8468-145">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-145">Guid</span></span>|  
|<span data-ttu-id="d8468-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d8468-146">COLUMN_PROPID</span></span>|<span data-ttu-id="d8468-147">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-147">Int64</span></span>|  
|<span data-ttu-id="d8468-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d8468-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="d8468-149">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-149">Int64</span></span>|  
|<span data-ttu-id="d8468-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="d8468-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="d8468-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-151">Boolean</span></span>|  
|<span data-ttu-id="d8468-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d8468-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="d8468-153">String</span><span class="sxs-lookup"><span data-stu-id="d8468-153">String</span></span>|  
|<span data-ttu-id="d8468-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d8468-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="d8468-155">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-155">Int64</span></span>|  
|<span data-ttu-id="d8468-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d8468-156">IS_NULLABLE</span></span>|<span data-ttu-id="d8468-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-157">Boolean</span></span>|  
|<span data-ttu-id="d8468-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8468-158">DATA_TYPE</span></span>|<span data-ttu-id="d8468-159">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-159">Int32</span></span>|  
|<span data-ttu-id="d8468-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-160">TYPE_GUID</span></span>|<span data-ttu-id="d8468-161">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-161">Guid</span></span>|  
|<span data-ttu-id="d8468-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d8468-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d8468-163">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-163">Int64</span></span>|  
|<span data-ttu-id="d8468-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d8468-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d8468-165">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-165">Int64</span></span>|  
|<span data-ttu-id="d8468-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d8468-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d8468-167">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-167">Int32</span></span>|  
|<span data-ttu-id="d8468-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d8468-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="d8468-169">Int16</span><span class="sxs-lookup"><span data-stu-id="d8468-169">Int16</span></span>|  
|<span data-ttu-id="d8468-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d8468-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="d8468-171">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-171">Int64</span></span>|  
|<span data-ttu-id="d8468-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="d8468-173">String</span><span class="sxs-lookup"><span data-stu-id="d8468-173">String</span></span>|  
|<span data-ttu-id="d8468-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="d8468-175">String</span><span class="sxs-lookup"><span data-stu-id="d8468-175">String</span></span>|  
|<span data-ttu-id="d8468-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="d8468-177">String</span><span class="sxs-lookup"><span data-stu-id="d8468-177">String</span></span>|  
|<span data-ttu-id="d8468-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="d8468-179">String</span><span class="sxs-lookup"><span data-stu-id="d8468-179">String</span></span>|  
|<span data-ttu-id="d8468-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="d8468-181">String</span><span class="sxs-lookup"><span data-stu-id="d8468-181">String</span></span>|  
|<span data-ttu-id="d8468-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-182">COLLATION_NAME</span></span>|<span data-ttu-id="d8468-183">String</span><span class="sxs-lookup"><span data-stu-id="d8468-183">String</span></span>|  
|<span data-ttu-id="d8468-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="d8468-185">String</span><span class="sxs-lookup"><span data-stu-id="d8468-185">String</span></span>|  
|<span data-ttu-id="d8468-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="d8468-187">String</span><span class="sxs-lookup"><span data-stu-id="d8468-187">String</span></span>|  
|<span data-ttu-id="d8468-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-188">DOMAIN_NAME</span></span>|<span data-ttu-id="d8468-189">String</span><span class="sxs-lookup"><span data-stu-id="d8468-189">String</span></span>|  
|<span data-ttu-id="d8468-190">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-190">DESCRIPTION</span></span>|<span data-ttu-id="d8468-191">String</span><span class="sxs-lookup"><span data-stu-id="d8468-191">String</span></span>|  
|<span data-ttu-id="d8468-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="d8468-192">COLUMN_LCID</span></span>|<span data-ttu-id="d8468-193">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-193">Int32</span></span>|  
|<span data-ttu-id="d8468-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="d8468-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="d8468-195">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-195">Int32</span></span>|  
|<span data-ttu-id="d8468-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="d8468-196">COLUMN_SORTID</span></span>|<span data-ttu-id="d8468-197">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-197">Int32</span></span>|  
|<span data-ttu-id="d8468-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="d8468-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="d8468-199">Byte]</span><span class="sxs-lookup"><span data-stu-id="d8468-199">Byte[]</span></span>|  
|<span data-ttu-id="d8468-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="d8468-200">IS_COMPUTED</span></span>|<span data-ttu-id="d8468-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d8468-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="d8468-202">Procedures</span></span>  
  
|<span data-ttu-id="d8468-203">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-203">ColumnName</span></span>|<span data-ttu-id="d8468-204">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d8468-206">String</span><span class="sxs-lookup"><span data-stu-id="d8468-206">String</span></span>|  
|<span data-ttu-id="d8468-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d8468-208">String</span><span class="sxs-lookup"><span data-stu-id="d8468-208">String</span></span>|  
|<span data-ttu-id="d8468-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="d8468-210">String</span><span class="sxs-lookup"><span data-stu-id="d8468-210">String</span></span>|  
|<span data-ttu-id="d8468-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8468-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d8468-212">Int16</span><span class="sxs-lookup"><span data-stu-id="d8468-212">Int16</span></span>|  
|<span data-ttu-id="d8468-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d8468-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="d8468-214">String</span><span class="sxs-lookup"><span data-stu-id="d8468-214">String</span></span>|  
|<span data-ttu-id="d8468-215">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-215">DESCRIPTION</span></span>|<span data-ttu-id="d8468-216">String</span><span class="sxs-lookup"><span data-stu-id="d8468-216">String</span></span>|  
|<span data-ttu-id="d8468-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d8468-217">DATE_CREATED</span></span>|<span data-ttu-id="d8468-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-218">DateTime</span></span>|  
|<span data-ttu-id="d8468-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d8468-219">DATE_MODIFIED</span></span>|<span data-ttu-id="d8468-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="d8468-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d8468-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="d8468-222">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-222">ColumnName</span></span>|<span data-ttu-id="d8468-223">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d8468-225">String</span><span class="sxs-lookup"><span data-stu-id="d8468-225">String</span></span>|  
|<span data-ttu-id="d8468-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d8468-227">String</span><span class="sxs-lookup"><span data-stu-id="d8468-227">String</span></span>|  
|<span data-ttu-id="d8468-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="d8468-229">String</span><span class="sxs-lookup"><span data-stu-id="d8468-229">String</span></span>|  
|<span data-ttu-id="d8468-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-230">PARAMETER_NAME</span></span>|<span data-ttu-id="d8468-231">String</span><span class="sxs-lookup"><span data-stu-id="d8468-231">String</span></span>|  
|<span data-ttu-id="d8468-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d8468-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="d8468-233">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-233">Int32</span></span>|  
|<span data-ttu-id="d8468-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8468-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="d8468-235">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-235">Int32</span></span>|  
|<span data-ttu-id="d8468-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="d8468-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="d8468-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-237">Boolean</span></span>|  
|<span data-ttu-id="d8468-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d8468-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="d8468-239">String</span><span class="sxs-lookup"><span data-stu-id="d8468-239">String</span></span>|  
|<span data-ttu-id="d8468-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d8468-240">IS_NULLABLE</span></span>|<span data-ttu-id="d8468-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-241">Boolean</span></span>|  
|<span data-ttu-id="d8468-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8468-242">DATA_TYPE</span></span>|<span data-ttu-id="d8468-243">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-243">Int32</span></span>|  
|<span data-ttu-id="d8468-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d8468-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d8468-245">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-245">Int64</span></span>|  
|<span data-ttu-id="d8468-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d8468-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d8468-247">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-247">Int64</span></span>|  
|<span data-ttu-id="d8468-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d8468-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d8468-249">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-249">Int32</span></span>|  
|<span data-ttu-id="d8468-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d8468-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="d8468-251">Int16</span><span class="sxs-lookup"><span data-stu-id="d8468-251">Int16</span></span>|  
|<span data-ttu-id="d8468-252">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-252">DESCRIPTION</span></span>|<span data-ttu-id="d8468-253">String</span><span class="sxs-lookup"><span data-stu-id="d8468-253">String</span></span>|  
|<span data-ttu-id="d8468-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-254">TYPE_NAME</span></span>|<span data-ttu-id="d8468-255">String</span><span class="sxs-lookup"><span data-stu-id="d8468-255">String</span></span>|  
|<span data-ttu-id="d8468-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="d8468-257">String</span><span class="sxs-lookup"><span data-stu-id="d8468-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="d8468-258">Katalogu</span><span class="sxs-lookup"><span data-stu-id="d8468-258">Catalog</span></span>  
  
|<span data-ttu-id="d8468-259">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-259">ColumnName</span></span>|<span data-ttu-id="d8468-260">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-261">CATALOG_NAME</span></span>|<span data-ttu-id="d8468-262">String</span><span class="sxs-lookup"><span data-stu-id="d8468-262">String</span></span>|  
|<span data-ttu-id="d8468-263">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-263">DESCRIPTION</span></span>|<span data-ttu-id="d8468-264">String</span><span class="sxs-lookup"><span data-stu-id="d8468-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="d8468-265">Indexy</span><span class="sxs-lookup"><span data-stu-id="d8468-265">Indexes</span></span>  
  
|<span data-ttu-id="d8468-266">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-266">ColumnName</span></span>|<span data-ttu-id="d8468-267">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-268">TABLE_CATALOG</span></span>|<span data-ttu-id="d8468-269">String</span><span class="sxs-lookup"><span data-stu-id="d8468-269">String</span></span>|  
|<span data-ttu-id="d8468-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8468-271">String</span><span class="sxs-lookup"><span data-stu-id="d8468-271">String</span></span>|  
|<span data-ttu-id="d8468-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-272">TABLE_NAME</span></span>|<span data-ttu-id="d8468-273">String</span><span class="sxs-lookup"><span data-stu-id="d8468-273">String</span></span>|  
|<span data-ttu-id="d8468-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-274">INDEX_CATALOG</span></span>|<span data-ttu-id="d8468-275">String</span><span class="sxs-lookup"><span data-stu-id="d8468-275">String</span></span>|  
|<span data-ttu-id="d8468-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="d8468-277">String</span><span class="sxs-lookup"><span data-stu-id="d8468-277">String</span></span>|  
|<span data-ttu-id="d8468-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-278">INDEX_NAME</span></span>|<span data-ttu-id="d8468-279">String</span><span class="sxs-lookup"><span data-stu-id="d8468-279">String</span></span>|  
|<span data-ttu-id="d8468-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="d8468-280">PRIMARY_KEY</span></span>|<span data-ttu-id="d8468-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-281">Boolean</span></span>|  
|<span data-ttu-id="d8468-282">JEDINEČNÉ</span><span class="sxs-lookup"><span data-stu-id="d8468-282">UNIQUE</span></span>|<span data-ttu-id="d8468-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-283">Boolean</span></span>|  
|<span data-ttu-id="d8468-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="d8468-284">CLUSTERED</span></span>|<span data-ttu-id="d8468-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-285">Boolean</span></span>|  
|<span data-ttu-id="d8468-286">TYP</span><span class="sxs-lookup"><span data-stu-id="d8468-286">TYPE</span></span>|<span data-ttu-id="d8468-287">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-287">Int32</span></span>|  
|<span data-ttu-id="d8468-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="d8468-288">FILL_FACTOR</span></span>|<span data-ttu-id="d8468-289">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-289">Int32</span></span>|  
|<span data-ttu-id="d8468-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="d8468-290">INITIAL_SIZE</span></span>|<span data-ttu-id="d8468-291">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-291">Int32</span></span>|  
|<span data-ttu-id="d8468-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="d8468-292">NULLS</span></span>|<span data-ttu-id="d8468-293">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-293">Int32</span></span>|  
|<span data-ttu-id="d8468-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="d8468-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="d8468-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-295">Boolean</span></span>|  
|<span data-ttu-id="d8468-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="d8468-296">AUTO_UPDATE</span></span>|<span data-ttu-id="d8468-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-297">Boolean</span></span>|  
|<span data-ttu-id="d8468-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="d8468-298">NULL_COLLATION</span></span>|<span data-ttu-id="d8468-299">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-299">Int32</span></span>|  
|<span data-ttu-id="d8468-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d8468-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="d8468-301">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-301">Int64</span></span>|  
|<span data-ttu-id="d8468-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-302">COLUMN_NAME</span></span>|<span data-ttu-id="d8468-303">String</span><span class="sxs-lookup"><span data-stu-id="d8468-303">String</span></span>|  
|<span data-ttu-id="d8468-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-304">COLUMN_GUID</span></span>|<span data-ttu-id="d8468-305">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-305">Guid</span></span>|  
|<span data-ttu-id="d8468-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d8468-306">COLUMN_PROPID</span></span>|<span data-ttu-id="d8468-307">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-307">Int64</span></span>|  
|<span data-ttu-id="d8468-308">KOLACE</span><span class="sxs-lookup"><span data-stu-id="d8468-308">COLLATION</span></span>|<span data-ttu-id="d8468-309">Int16</span><span class="sxs-lookup"><span data-stu-id="d8468-309">Int16</span></span>|  
|<span data-ttu-id="d8468-310">MOHUTNOST</span><span class="sxs-lookup"><span data-stu-id="d8468-310">CARDINALITY</span></span>|<span data-ttu-id="d8468-311">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="d8468-311">Decimal</span></span>|  
|<span data-ttu-id="d8468-312">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="d8468-312">PAGES</span></span>|<span data-ttu-id="d8468-313">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-313">Int32</span></span>|  
|<span data-ttu-id="d8468-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="d8468-314">FILTER_CONDITION</span></span>|<span data-ttu-id="d8468-315">String</span><span class="sxs-lookup"><span data-stu-id="d8468-315">String</span></span>|  
|<span data-ttu-id="d8468-316">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="d8468-316">INTEGRATED</span></span>|<span data-ttu-id="d8468-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="d8468-318">Zprostředkovatel OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="d8468-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="d8468-319">Oracle OLE DB ovladače Microsoft podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="d8468-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="d8468-320">Tabulky</span><span class="sxs-lookup"><span data-stu-id="d8468-320">Tables</span></span>  
  
-   <span data-ttu-id="d8468-321">Sloupce</span><span class="sxs-lookup"><span data-stu-id="d8468-321">Columns</span></span>  
  
-   <span data-ttu-id="d8468-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="d8468-322">Procedures</span></span>  
  
-   <span data-ttu-id="d8468-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d8468-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="d8468-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d8468-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="d8468-325">zobrazení</span><span class="sxs-lookup"><span data-stu-id="d8468-325">Views</span></span>  
  
-   <span data-ttu-id="d8468-326">Indexy</span><span class="sxs-lookup"><span data-stu-id="d8468-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="d8468-327">Tabulky</span><span class="sxs-lookup"><span data-stu-id="d8468-327">Tables</span></span>  
  
|<span data-ttu-id="d8468-328">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-328">ColumnName</span></span>|<span data-ttu-id="d8468-329">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-330">TABLE_CATALOG</span></span>|<span data-ttu-id="d8468-331">String</span><span class="sxs-lookup"><span data-stu-id="d8468-331">String</span></span>|  
|<span data-ttu-id="d8468-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8468-333">String</span><span class="sxs-lookup"><span data-stu-id="d8468-333">String</span></span>|  
|<span data-ttu-id="d8468-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-334">TABLE_NAME</span></span>|<span data-ttu-id="d8468-335">String</span><span class="sxs-lookup"><span data-stu-id="d8468-335">String</span></span>|  
|<span data-ttu-id="d8468-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8468-336">TABLE_TYPE</span></span>|<span data-ttu-id="d8468-337">String</span><span class="sxs-lookup"><span data-stu-id="d8468-337">String</span></span>|  
|<span data-ttu-id="d8468-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-338">TABLE_GUID</span></span>|<span data-ttu-id="d8468-339">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-339">Guid</span></span>|  
|<span data-ttu-id="d8468-340">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-340">DESCRIPTION</span></span>|<span data-ttu-id="d8468-341">String</span><span class="sxs-lookup"><span data-stu-id="d8468-341">String</span></span>|  
|<span data-ttu-id="d8468-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="d8468-342">TABLE_PROPID</span></span>|<span data-ttu-id="d8468-343">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-343">Int64</span></span>|  
|<span data-ttu-id="d8468-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d8468-344">DATE_CREATED</span></span>|<span data-ttu-id="d8468-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-345">DateTime</span></span>|  
|<span data-ttu-id="d8468-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d8468-346">DATE_MODIFIED</span></span>|<span data-ttu-id="d8468-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d8468-348">Sloupce</span><span class="sxs-lookup"><span data-stu-id="d8468-348">Columns</span></span>  
  
|<span data-ttu-id="d8468-349">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-349">ColumnName</span></span>|<span data-ttu-id="d8468-350">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-351">TABLE_CATALOG</span></span>|<span data-ttu-id="d8468-352">String</span><span class="sxs-lookup"><span data-stu-id="d8468-352">String</span></span>|  
|<span data-ttu-id="d8468-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8468-354">String</span><span class="sxs-lookup"><span data-stu-id="d8468-354">String</span></span>|  
|<span data-ttu-id="d8468-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-355">TABLE_NAME</span></span>|<span data-ttu-id="d8468-356">String</span><span class="sxs-lookup"><span data-stu-id="d8468-356">String</span></span>|  
|<span data-ttu-id="d8468-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-357">COLUMN_NAME</span></span>|<span data-ttu-id="d8468-358">String</span><span class="sxs-lookup"><span data-stu-id="d8468-358">String</span></span>|  
|<span data-ttu-id="d8468-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-359">COLUMN_GUID</span></span>|<span data-ttu-id="d8468-360">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-360">Guid</span></span>|  
|<span data-ttu-id="d8468-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d8468-361">COLUMN_PROPID</span></span>|<span data-ttu-id="d8468-362">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-362">Int64</span></span>|  
|<span data-ttu-id="d8468-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d8468-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="d8468-364">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-364">Int64</span></span>|  
|<span data-ttu-id="d8468-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="d8468-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="d8468-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-366">Boolean</span></span>|  
|<span data-ttu-id="d8468-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d8468-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="d8468-368">String</span><span class="sxs-lookup"><span data-stu-id="d8468-368">String</span></span>|  
|<span data-ttu-id="d8468-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d8468-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="d8468-370">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-370">Int64</span></span>|  
|<span data-ttu-id="d8468-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d8468-371">IS_NULLABLE</span></span>|<span data-ttu-id="d8468-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-372">Boolean</span></span>|  
|<span data-ttu-id="d8468-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8468-373">DATA_TYPE</span></span>|<span data-ttu-id="d8468-374">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-374">Int32</span></span>|  
|<span data-ttu-id="d8468-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-375">TYPE_GUID</span></span>|<span data-ttu-id="d8468-376">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-376">Guid</span></span>|  
|<span data-ttu-id="d8468-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d8468-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d8468-378">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-378">Int64</span></span>|  
|<span data-ttu-id="d8468-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d8468-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d8468-380">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-380">Int64</span></span>|  
|<span data-ttu-id="d8468-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d8468-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d8468-382">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-382">Int32</span></span>|  
|<span data-ttu-id="d8468-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d8468-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="d8468-384">Int16</span><span class="sxs-lookup"><span data-stu-id="d8468-384">Int16</span></span>|  
|<span data-ttu-id="d8468-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d8468-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="d8468-386">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-386">Int64</span></span>|  
|<span data-ttu-id="d8468-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="d8468-388">String</span><span class="sxs-lookup"><span data-stu-id="d8468-388">String</span></span>|  
|<span data-ttu-id="d8468-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="d8468-390">String</span><span class="sxs-lookup"><span data-stu-id="d8468-390">String</span></span>|  
|<span data-ttu-id="d8468-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="d8468-392">String</span><span class="sxs-lookup"><span data-stu-id="d8468-392">String</span></span>|  
|<span data-ttu-id="d8468-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="d8468-394">String</span><span class="sxs-lookup"><span data-stu-id="d8468-394">String</span></span>|  
|<span data-ttu-id="d8468-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="d8468-396">String</span><span class="sxs-lookup"><span data-stu-id="d8468-396">String</span></span>|  
|<span data-ttu-id="d8468-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-397">COLLATION_NAME</span></span>|<span data-ttu-id="d8468-398">String</span><span class="sxs-lookup"><span data-stu-id="d8468-398">String</span></span>|  
|<span data-ttu-id="d8468-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="d8468-400">String</span><span class="sxs-lookup"><span data-stu-id="d8468-400">String</span></span>|  
|<span data-ttu-id="d8468-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="d8468-402">String</span><span class="sxs-lookup"><span data-stu-id="d8468-402">String</span></span>|  
|<span data-ttu-id="d8468-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-403">DOMAIN_NAME</span></span>|<span data-ttu-id="d8468-404">String</span><span class="sxs-lookup"><span data-stu-id="d8468-404">String</span></span>|  
|<span data-ttu-id="d8468-405">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-405">DESCRIPTION</span></span>|<span data-ttu-id="d8468-406">String</span><span class="sxs-lookup"><span data-stu-id="d8468-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d8468-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="d8468-407">Procedures</span></span>  
  
|<span data-ttu-id="d8468-408">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-408">ColumnName</span></span>|<span data-ttu-id="d8468-409">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d8468-411">String</span><span class="sxs-lookup"><span data-stu-id="d8468-411">String</span></span>|  
|<span data-ttu-id="d8468-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d8468-413">String</span><span class="sxs-lookup"><span data-stu-id="d8468-413">String</span></span>|  
|<span data-ttu-id="d8468-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="d8468-415">String</span><span class="sxs-lookup"><span data-stu-id="d8468-415">String</span></span>|  
|<span data-ttu-id="d8468-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8468-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d8468-417">Int16</span><span class="sxs-lookup"><span data-stu-id="d8468-417">Int16</span></span>|  
|<span data-ttu-id="d8468-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d8468-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="d8468-419">String</span><span class="sxs-lookup"><span data-stu-id="d8468-419">String</span></span>|  
|<span data-ttu-id="d8468-420">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-420">DESCRIPTION</span></span>|<span data-ttu-id="d8468-421">String</span><span class="sxs-lookup"><span data-stu-id="d8468-421">String</span></span>|  
|<span data-ttu-id="d8468-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d8468-422">DATE_CREATED</span></span>|<span data-ttu-id="d8468-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-423">DateTime</span></span>|  
|<span data-ttu-id="d8468-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d8468-424">DATE_MODIFIED</span></span>|<span data-ttu-id="d8468-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="d8468-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d8468-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="d8468-427">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-427">ColumnName</span></span>|<span data-ttu-id="d8468-428">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d8468-430">String</span><span class="sxs-lookup"><span data-stu-id="d8468-430">String</span></span>|  
|<span data-ttu-id="d8468-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d8468-432">String</span><span class="sxs-lookup"><span data-stu-id="d8468-432">String</span></span>|  
|<span data-ttu-id="d8468-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="d8468-434">String</span><span class="sxs-lookup"><span data-stu-id="d8468-434">String</span></span>|  
|<span data-ttu-id="d8468-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-435">COLUMN_NAME</span></span>|<span data-ttu-id="d8468-436">String</span><span class="sxs-lookup"><span data-stu-id="d8468-436">String</span></span>|  
|<span data-ttu-id="d8468-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-437">COLUMN_GUID</span></span>|<span data-ttu-id="d8468-438">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-438">Guid</span></span>|  
|<span data-ttu-id="d8468-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d8468-439">COLUMN_PROPID</span></span>|<span data-ttu-id="d8468-440">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-440">Int64</span></span>|  
|<span data-ttu-id="d8468-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="d8468-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="d8468-442">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-442">Int64</span></span>|  
|<span data-ttu-id="d8468-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d8468-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="d8468-444">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-444">Int64</span></span>|  
|<span data-ttu-id="d8468-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d8468-445">IS_NULLABLE</span></span>|<span data-ttu-id="d8468-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-446">Boolean</span></span>|  
|<span data-ttu-id="d8468-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8468-447">DATA_TYPE</span></span>|<span data-ttu-id="d8468-448">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-448">Int32</span></span>|  
|<span data-ttu-id="d8468-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-449">TYPE_GUID</span></span>|<span data-ttu-id="d8468-450">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-450">Guid</span></span>|  
|<span data-ttu-id="d8468-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d8468-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d8468-452">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-452">Int64</span></span>|  
|<span data-ttu-id="d8468-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d8468-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d8468-454">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-454">Int64</span></span>|  
|<span data-ttu-id="d8468-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d8468-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d8468-456">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-456">Int32</span></span>|  
|<span data-ttu-id="d8468-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d8468-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="d8468-458">Int16</span><span class="sxs-lookup"><span data-stu-id="d8468-458">Int16</span></span>|  
|<span data-ttu-id="d8468-459">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-459">DESCRIPTION</span></span>|<span data-ttu-id="d8468-460">String</span><span class="sxs-lookup"><span data-stu-id="d8468-460">String</span></span>|  
|<span data-ttu-id="d8468-461">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="d8468-461">OVERLOAD</span></span>|<span data-ttu-id="d8468-462">Int16</span><span class="sxs-lookup"><span data-stu-id="d8468-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="d8468-463">zobrazení</span><span class="sxs-lookup"><span data-stu-id="d8468-463">Views</span></span>  
  
|<span data-ttu-id="d8468-464">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-464">ColumnName</span></span>|<span data-ttu-id="d8468-465">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-466">TABLE_CATALOG</span></span>|<span data-ttu-id="d8468-467">String</span><span class="sxs-lookup"><span data-stu-id="d8468-467">String</span></span>|  
|<span data-ttu-id="d8468-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8468-469">String</span><span class="sxs-lookup"><span data-stu-id="d8468-469">String</span></span>|  
|<span data-ttu-id="d8468-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-470">TABLE_NAME</span></span>|<span data-ttu-id="d8468-471">String</span><span class="sxs-lookup"><span data-stu-id="d8468-471">String</span></span>|  
|<span data-ttu-id="d8468-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d8468-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="d8468-473">String</span><span class="sxs-lookup"><span data-stu-id="d8468-473">String</span></span>|  
|<span data-ttu-id="d8468-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="d8468-474">CHECK_OPTION</span></span>|<span data-ttu-id="d8468-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-475">Boolean</span></span>|  
|<span data-ttu-id="d8468-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="d8468-476">IS_UPDATABLE</span></span>|<span data-ttu-id="d8468-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-477">Boolean</span></span>|  
|<span data-ttu-id="d8468-478">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-478">DESCRIPTION</span></span>|<span data-ttu-id="d8468-479">String</span><span class="sxs-lookup"><span data-stu-id="d8468-479">String</span></span>|  
|<span data-ttu-id="d8468-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d8468-480">DATE_CREATED</span></span>|<span data-ttu-id="d8468-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-481">DateTime</span></span>|  
|<span data-ttu-id="d8468-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d8468-482">DATE_MODIFIED</span></span>|<span data-ttu-id="d8468-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="d8468-484">Indexy</span><span class="sxs-lookup"><span data-stu-id="d8468-484">Indexes</span></span>  
  
|<span data-ttu-id="d8468-485">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-485">ColumnName</span></span>|<span data-ttu-id="d8468-486">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-487">TABLE_CATALOG</span></span>|<span data-ttu-id="d8468-488">String</span><span class="sxs-lookup"><span data-stu-id="d8468-488">String</span></span>|  
|<span data-ttu-id="d8468-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8468-490">String</span><span class="sxs-lookup"><span data-stu-id="d8468-490">String</span></span>|  
|<span data-ttu-id="d8468-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-491">TABLE_NAME</span></span>|<span data-ttu-id="d8468-492">String</span><span class="sxs-lookup"><span data-stu-id="d8468-492">String</span></span>|  
|<span data-ttu-id="d8468-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-493">INDEX_CATALOG</span></span>|<span data-ttu-id="d8468-494">String</span><span class="sxs-lookup"><span data-stu-id="d8468-494">String</span></span>|  
|<span data-ttu-id="d8468-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="d8468-496">String</span><span class="sxs-lookup"><span data-stu-id="d8468-496">String</span></span>|  
|<span data-ttu-id="d8468-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-497">INDEX_NAME</span></span>|<span data-ttu-id="d8468-498">String</span><span class="sxs-lookup"><span data-stu-id="d8468-498">String</span></span>|  
|<span data-ttu-id="d8468-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="d8468-499">PRIMARY_KEY</span></span>|<span data-ttu-id="d8468-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-500">Boolean</span></span>|  
|<span data-ttu-id="d8468-501">JEDINEČNÉ</span><span class="sxs-lookup"><span data-stu-id="d8468-501">UNIQUE</span></span>|<span data-ttu-id="d8468-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-502">Boolean</span></span>|  
|<span data-ttu-id="d8468-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="d8468-503">CLUSTERED</span></span>|<span data-ttu-id="d8468-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-504">Boolean</span></span>|  
|<span data-ttu-id="d8468-505">TYP</span><span class="sxs-lookup"><span data-stu-id="d8468-505">TYPE</span></span>|<span data-ttu-id="d8468-506">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-506">Int32</span></span>|  
|<span data-ttu-id="d8468-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="d8468-507">FILL_FACTOR</span></span>|<span data-ttu-id="d8468-508">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-508">Int32</span></span>|  
|<span data-ttu-id="d8468-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="d8468-509">INITIAL_SIZE</span></span>|<span data-ttu-id="d8468-510">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-510">Int32</span></span>|  
|<span data-ttu-id="d8468-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="d8468-511">NULLS</span></span>|<span data-ttu-id="d8468-512">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-512">Int32</span></span>|  
|<span data-ttu-id="d8468-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="d8468-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="d8468-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-514">Boolean</span></span>|  
|<span data-ttu-id="d8468-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="d8468-515">AUTO_UPDATE</span></span>|<span data-ttu-id="d8468-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-516">Boolean</span></span>|  
|<span data-ttu-id="d8468-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="d8468-517">NULL_COLLATION</span></span>|<span data-ttu-id="d8468-518">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-518">Int32</span></span>|  
|<span data-ttu-id="d8468-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d8468-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="d8468-520">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-520">Int64</span></span>|  
|<span data-ttu-id="d8468-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-521">COLUMN_NAME</span></span>|<span data-ttu-id="d8468-522">String</span><span class="sxs-lookup"><span data-stu-id="d8468-522">String</span></span>|  
|<span data-ttu-id="d8468-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-523">COLUMN_GUID</span></span>|<span data-ttu-id="d8468-524">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-524">Guid</span></span>|  
|<span data-ttu-id="d8468-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d8468-525">COLUMN_PROPID</span></span>|<span data-ttu-id="d8468-526">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-526">Int64</span></span>|  
|<span data-ttu-id="d8468-527">KOLACE</span><span class="sxs-lookup"><span data-stu-id="d8468-527">COLLATION</span></span>|<span data-ttu-id="d8468-528">Int16</span><span class="sxs-lookup"><span data-stu-id="d8468-528">Int16</span></span>|  
|<span data-ttu-id="d8468-529">MOHUTNOST</span><span class="sxs-lookup"><span data-stu-id="d8468-529">CARDINALITY</span></span>|<span data-ttu-id="d8468-530">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="d8468-530">Decimal</span></span>|  
|<span data-ttu-id="d8468-531">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="d8468-531">PAGES</span></span>|<span data-ttu-id="d8468-532">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-532">Int32</span></span>|  
|<span data-ttu-id="d8468-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="d8468-533">FILTER_CONDITION</span></span>|<span data-ttu-id="d8468-534">String</span><span class="sxs-lookup"><span data-stu-id="d8468-534">String</span></span>|  
|<span data-ttu-id="d8468-535">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="d8468-535">INTEGRATED</span></span>|<span data-ttu-id="d8468-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="d8468-537">Zprostředkovatel Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="d8468-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="d8468-538">Microsoft Jet OLE DB ovladač podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="d8468-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="d8468-539">Tabulky</span><span class="sxs-lookup"><span data-stu-id="d8468-539">Tables</span></span>  
  
-   <span data-ttu-id="d8468-540">Sloupce</span><span class="sxs-lookup"><span data-stu-id="d8468-540">Columns</span></span>  
  
-   <span data-ttu-id="d8468-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="d8468-541">Procedures</span></span>  
  
-   <span data-ttu-id="d8468-542">zobrazení</span><span class="sxs-lookup"><span data-stu-id="d8468-542">Views</span></span>  
  
-   <span data-ttu-id="d8468-543">Indexy</span><span class="sxs-lookup"><span data-stu-id="d8468-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="d8468-544">Tabulky</span><span class="sxs-lookup"><span data-stu-id="d8468-544">Tables</span></span>  
  
|<span data-ttu-id="d8468-545">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-545">ColumnName</span></span>|<span data-ttu-id="d8468-546">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-547">TABLE_CATALOG</span></span>|<span data-ttu-id="d8468-548">String</span><span class="sxs-lookup"><span data-stu-id="d8468-548">String</span></span>|  
|<span data-ttu-id="d8468-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8468-550">String</span><span class="sxs-lookup"><span data-stu-id="d8468-550">String</span></span>|  
|<span data-ttu-id="d8468-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-551">TABLE_NAME</span></span>|<span data-ttu-id="d8468-552">String</span><span class="sxs-lookup"><span data-stu-id="d8468-552">String</span></span>|  
|<span data-ttu-id="d8468-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8468-553">TABLE_TYPE</span></span>|<span data-ttu-id="d8468-554">String</span><span class="sxs-lookup"><span data-stu-id="d8468-554">String</span></span>|  
|<span data-ttu-id="d8468-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-555">TABLE_GUID</span></span>|<span data-ttu-id="d8468-556">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-556">Guid</span></span>|  
|<span data-ttu-id="d8468-557">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-557">DESCRIPTION</span></span>|<span data-ttu-id="d8468-558">String</span><span class="sxs-lookup"><span data-stu-id="d8468-558">String</span></span>|  
|<span data-ttu-id="d8468-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="d8468-559">TABLE_PROPID</span></span>|<span data-ttu-id="d8468-560">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-560">Int64</span></span>|  
|<span data-ttu-id="d8468-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d8468-561">DATE_CREATED</span></span>|<span data-ttu-id="d8468-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-562">DateTime</span></span>|  
|<span data-ttu-id="d8468-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d8468-563">DATE_MODIFIED</span></span>|<span data-ttu-id="d8468-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d8468-565">Sloupce</span><span class="sxs-lookup"><span data-stu-id="d8468-565">Columns</span></span>  
  
|<span data-ttu-id="d8468-566">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-566">ColumnName</span></span>|<span data-ttu-id="d8468-567">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-568">TABLE_CATALOG</span></span>|<span data-ttu-id="d8468-569">String</span><span class="sxs-lookup"><span data-stu-id="d8468-569">String</span></span>|  
|<span data-ttu-id="d8468-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8468-571">String</span><span class="sxs-lookup"><span data-stu-id="d8468-571">String</span></span>|  
|<span data-ttu-id="d8468-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-572">TABLE_NAME</span></span>|<span data-ttu-id="d8468-573">String</span><span class="sxs-lookup"><span data-stu-id="d8468-573">String</span></span>|  
|<span data-ttu-id="d8468-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-574">COLUMN_NAME</span></span>|<span data-ttu-id="d8468-575">String</span><span class="sxs-lookup"><span data-stu-id="d8468-575">String</span></span>|  
|<span data-ttu-id="d8468-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-576">COLUMN_GUID</span></span>|<span data-ttu-id="d8468-577">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-577">Guid</span></span>|  
|<span data-ttu-id="d8468-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d8468-578">COLUMN_PROPID</span></span>|<span data-ttu-id="d8468-579">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-579">Int64</span></span>|  
|<span data-ttu-id="d8468-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d8468-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="d8468-581">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-581">Int64</span></span>|  
|<span data-ttu-id="d8468-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="d8468-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="d8468-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-583">Boolean</span></span>|  
|<span data-ttu-id="d8468-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d8468-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="d8468-585">String</span><span class="sxs-lookup"><span data-stu-id="d8468-585">String</span></span>|  
|<span data-ttu-id="d8468-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d8468-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="d8468-587">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-587">Int64</span></span>|  
|<span data-ttu-id="d8468-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d8468-588">IS_NULLABLE</span></span>|<span data-ttu-id="d8468-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-589">Boolean</span></span>|  
|<span data-ttu-id="d8468-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8468-590">DATA_TYPE</span></span>|<span data-ttu-id="d8468-591">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-591">Int32</span></span>|  
|<span data-ttu-id="d8468-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-592">TYPE_GUID</span></span>|<span data-ttu-id="d8468-593">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-593">Guid</span></span>|  
|<span data-ttu-id="d8468-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d8468-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="d8468-595">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-595">Int64</span></span>|  
|<span data-ttu-id="d8468-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d8468-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="d8468-597">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-597">Int64</span></span>|  
|<span data-ttu-id="d8468-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d8468-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="d8468-599">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-599">Int32</span></span>|  
|<span data-ttu-id="d8468-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="d8468-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="d8468-601">Int16</span><span class="sxs-lookup"><span data-stu-id="d8468-601">Int16</span></span>|  
|<span data-ttu-id="d8468-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="d8468-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="d8468-603">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-603">Int64</span></span>|  
|<span data-ttu-id="d8468-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="d8468-605">String</span><span class="sxs-lookup"><span data-stu-id="d8468-605">String</span></span>|  
|<span data-ttu-id="d8468-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="d8468-607">String</span><span class="sxs-lookup"><span data-stu-id="d8468-607">String</span></span>|  
|<span data-ttu-id="d8468-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="d8468-609">String</span><span class="sxs-lookup"><span data-stu-id="d8468-609">String</span></span>|  
|<span data-ttu-id="d8468-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="d8468-611">String</span><span class="sxs-lookup"><span data-stu-id="d8468-611">String</span></span>|  
|<span data-ttu-id="d8468-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="d8468-613">String</span><span class="sxs-lookup"><span data-stu-id="d8468-613">String</span></span>|  
|<span data-ttu-id="d8468-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-614">COLLATION_NAME</span></span>|<span data-ttu-id="d8468-615">String</span><span class="sxs-lookup"><span data-stu-id="d8468-615">String</span></span>|  
|<span data-ttu-id="d8468-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="d8468-617">String</span><span class="sxs-lookup"><span data-stu-id="d8468-617">String</span></span>|  
|<span data-ttu-id="d8468-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="d8468-619">String</span><span class="sxs-lookup"><span data-stu-id="d8468-619">String</span></span>|  
|<span data-ttu-id="d8468-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-620">DOMAIN_NAME</span></span>|<span data-ttu-id="d8468-621">String</span><span class="sxs-lookup"><span data-stu-id="d8468-621">String</span></span>|  
|<span data-ttu-id="d8468-622">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-622">DESCRIPTION</span></span>|<span data-ttu-id="d8468-623">String</span><span class="sxs-lookup"><span data-stu-id="d8468-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d8468-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="d8468-624">Procedures</span></span>  
  
|<span data-ttu-id="d8468-625">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-625">ColumnName</span></span>|<span data-ttu-id="d8468-626">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="d8468-628">String</span><span class="sxs-lookup"><span data-stu-id="d8468-628">String</span></span>|  
|<span data-ttu-id="d8468-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="d8468-630">String</span><span class="sxs-lookup"><span data-stu-id="d8468-630">String</span></span>|  
|<span data-ttu-id="d8468-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="d8468-632">String</span><span class="sxs-lookup"><span data-stu-id="d8468-632">String</span></span>|  
|<span data-ttu-id="d8468-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8468-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d8468-634">Int16</span><span class="sxs-lookup"><span data-stu-id="d8468-634">Int16</span></span>|  
|<span data-ttu-id="d8468-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d8468-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="d8468-636">String</span><span class="sxs-lookup"><span data-stu-id="d8468-636">String</span></span>|  
|<span data-ttu-id="d8468-637">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-637">DESCRIPTION</span></span>|<span data-ttu-id="d8468-638">String</span><span class="sxs-lookup"><span data-stu-id="d8468-638">String</span></span>|  
|<span data-ttu-id="d8468-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d8468-639">DATE_CREATED</span></span>|<span data-ttu-id="d8468-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-640">DateTime</span></span>|  
|<span data-ttu-id="d8468-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d8468-641">DATE_MODIFIED</span></span>|<span data-ttu-id="d8468-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="d8468-643">zobrazení</span><span class="sxs-lookup"><span data-stu-id="d8468-643">Views</span></span>  
  
|<span data-ttu-id="d8468-644">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-644">ColumnName</span></span>|<span data-ttu-id="d8468-645">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-646">TABLE_CATALOG</span></span>|<span data-ttu-id="d8468-647">String</span><span class="sxs-lookup"><span data-stu-id="d8468-647">String</span></span>|  
|<span data-ttu-id="d8468-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8468-649">String</span><span class="sxs-lookup"><span data-stu-id="d8468-649">String</span></span>|  
|<span data-ttu-id="d8468-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-650">TABLE_NAME</span></span>|<span data-ttu-id="d8468-651">String</span><span class="sxs-lookup"><span data-stu-id="d8468-651">String</span></span>|  
|<span data-ttu-id="d8468-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="d8468-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="d8468-653">String</span><span class="sxs-lookup"><span data-stu-id="d8468-653">String</span></span>|  
|<span data-ttu-id="d8468-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="d8468-654">CHECK_OPTION</span></span>|<span data-ttu-id="d8468-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-655">Boolean</span></span>|  
|<span data-ttu-id="d8468-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="d8468-656">IS_UPDATABLE</span></span>|<span data-ttu-id="d8468-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-657">Boolean</span></span>|  
|<span data-ttu-id="d8468-658">POPIS</span><span class="sxs-lookup"><span data-stu-id="d8468-658">DESCRIPTION</span></span>|<span data-ttu-id="d8468-659">String</span><span class="sxs-lookup"><span data-stu-id="d8468-659">String</span></span>|  
|<span data-ttu-id="d8468-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="d8468-660">DATE_CREATED</span></span>|<span data-ttu-id="d8468-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-661">DateTime</span></span>|  
|<span data-ttu-id="d8468-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="d8468-662">DATE_MODIFIED</span></span>|<span data-ttu-id="d8468-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="d8468-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="d8468-664">Indexy</span><span class="sxs-lookup"><span data-stu-id="d8468-664">Indexes</span></span>  
  
|<span data-ttu-id="d8468-665">columnName</span><span class="sxs-lookup"><span data-stu-id="d8468-665">ColumnName</span></span>|<span data-ttu-id="d8468-666">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d8468-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d8468-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-667">TABLE_CATALOG</span></span>|<span data-ttu-id="d8468-668">String</span><span class="sxs-lookup"><span data-stu-id="d8468-668">String</span></span>|  
|<span data-ttu-id="d8468-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8468-670">String</span><span class="sxs-lookup"><span data-stu-id="d8468-670">String</span></span>|  
|<span data-ttu-id="d8468-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-671">TABLE_NAME</span></span>|<span data-ttu-id="d8468-672">String</span><span class="sxs-lookup"><span data-stu-id="d8468-672">String</span></span>|  
|<span data-ttu-id="d8468-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8468-673">INDEX_CATALOG</span></span>|<span data-ttu-id="d8468-674">String</span><span class="sxs-lookup"><span data-stu-id="d8468-674">String</span></span>|  
|<span data-ttu-id="d8468-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8468-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="d8468-676">String</span><span class="sxs-lookup"><span data-stu-id="d8468-676">String</span></span>|  
|<span data-ttu-id="d8468-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-677">INDEX_NAME</span></span>|<span data-ttu-id="d8468-678">String</span><span class="sxs-lookup"><span data-stu-id="d8468-678">String</span></span>|  
|<span data-ttu-id="d8468-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="d8468-679">PRIMARY_KEY</span></span>|<span data-ttu-id="d8468-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-680">Boolean</span></span>|  
|<span data-ttu-id="d8468-681">JEDINEČNÉ</span><span class="sxs-lookup"><span data-stu-id="d8468-681">UNIQUE</span></span>|<span data-ttu-id="d8468-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-682">Boolean</span></span>|  
|<span data-ttu-id="d8468-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="d8468-683">CLUSTERED</span></span>|<span data-ttu-id="d8468-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-684">Boolean</span></span>|  
|<span data-ttu-id="d8468-685">TYP</span><span class="sxs-lookup"><span data-stu-id="d8468-685">TYPE</span></span>|<span data-ttu-id="d8468-686">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-686">Int32</span></span>|  
|<span data-ttu-id="d8468-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="d8468-687">FILL_FACTOR</span></span>|<span data-ttu-id="d8468-688">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-688">Int32</span></span>|  
|<span data-ttu-id="d8468-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="d8468-689">INITIAL_SIZE</span></span>|<span data-ttu-id="d8468-690">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-690">Int32</span></span>|  
|<span data-ttu-id="d8468-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="d8468-691">NULLS</span></span>|<span data-ttu-id="d8468-692">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-692">Int32</span></span>|  
|<span data-ttu-id="d8468-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="d8468-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="d8468-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-694">Boolean</span></span>|  
|<span data-ttu-id="d8468-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="d8468-695">AUTO_UPDATE</span></span>|<span data-ttu-id="d8468-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-696">Boolean</span></span>|  
|<span data-ttu-id="d8468-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="d8468-697">NULL_COLLATION</span></span>|<span data-ttu-id="d8468-698">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-698">Int32</span></span>|  
|<span data-ttu-id="d8468-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d8468-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="d8468-700">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-700">Int64</span></span>|  
|<span data-ttu-id="d8468-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8468-701">COLUMN_NAME</span></span>|<span data-ttu-id="d8468-702">String</span><span class="sxs-lookup"><span data-stu-id="d8468-702">String</span></span>|  
|<span data-ttu-id="d8468-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-703">COLUMN_GUID</span></span>|<span data-ttu-id="d8468-704">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="d8468-704">Guid</span></span>|  
|<span data-ttu-id="d8468-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="d8468-705">COLUMN_PROPID</span></span>|<span data-ttu-id="d8468-706">Int64</span><span class="sxs-lookup"><span data-stu-id="d8468-706">Int64</span></span>|  
|<span data-ttu-id="d8468-707">KOLACE</span><span class="sxs-lookup"><span data-stu-id="d8468-707">COLLATION</span></span>|<span data-ttu-id="d8468-708">Int16</span><span class="sxs-lookup"><span data-stu-id="d8468-708">Int16</span></span>|  
|<span data-ttu-id="d8468-709">MOHUTNOST</span><span class="sxs-lookup"><span data-stu-id="d8468-709">CARDINALITY</span></span>|<span data-ttu-id="d8468-710">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="d8468-710">Decimal</span></span>|  
|<span data-ttu-id="d8468-711">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="d8468-711">PAGES</span></span>|<span data-ttu-id="d8468-712">Int32</span><span class="sxs-lookup"><span data-stu-id="d8468-712">Int32</span></span>|  
|<span data-ttu-id="d8468-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="d8468-713">FILTER_CONDITION</span></span>|<span data-ttu-id="d8468-714">String</span><span class="sxs-lookup"><span data-stu-id="d8468-714">String</span></span>|  
|<span data-ttu-id="d8468-715">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="d8468-715">INTEGRATED</span></span>|<span data-ttu-id="d8468-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8468-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8468-717">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8468-717">See Also</span></span>  
 [<span data-ttu-id="d8468-718">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="d8468-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
