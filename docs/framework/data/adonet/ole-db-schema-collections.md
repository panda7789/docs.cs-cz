---
title: Kolekce schémat OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 2d5718c12100ebea49a6b6fab29a3790918c6ad3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783445"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="78b36-102">Kolekce schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="78b36-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="78b36-103">Tato část pojednává o podpoře kolekcí schémat pro poskytovatele OLE DB pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="78b36-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="78b36-104">Poskytovatel Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="78b36-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="78b36-105">Ovladač Microsoft SQL Server OLE DB podporuje kromě běžných kolekcí schémat následující konkrétní kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="78b36-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="78b36-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="78b36-106">Tables</span></span>  
  
- <span data-ttu-id="78b36-107">Sloupce</span><span class="sxs-lookup"><span data-stu-id="78b36-107">Columns</span></span>  
  
- <span data-ttu-id="78b36-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="78b36-108">Procedures</span></span>  
  
- <span data-ttu-id="78b36-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="78b36-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="78b36-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="78b36-110">Catalog</span></span>  
  
- <span data-ttu-id="78b36-111">Indexy</span><span class="sxs-lookup"><span data-stu-id="78b36-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="78b36-112">Tabulky</span><span class="sxs-lookup"><span data-stu-id="78b36-112">Tables</span></span>  
  
|<span data-ttu-id="78b36-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-113">ColumnName</span></span>|<span data-ttu-id="78b36-114">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-115">TABLE_CATALOG</span></span>|<span data-ttu-id="78b36-116">String</span><span class="sxs-lookup"><span data-stu-id="78b36-116">String</span></span>|  
|<span data-ttu-id="78b36-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="78b36-118">String</span><span class="sxs-lookup"><span data-stu-id="78b36-118">String</span></span>|  
|<span data-ttu-id="78b36-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-119">TABLE_NAME</span></span>|<span data-ttu-id="78b36-120">String</span><span class="sxs-lookup"><span data-stu-id="78b36-120">String</span></span>|  
|<span data-ttu-id="78b36-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="78b36-121">TABLE_TYPE</span></span>|<span data-ttu-id="78b36-122">String</span><span class="sxs-lookup"><span data-stu-id="78b36-122">String</span></span>|  
|<span data-ttu-id="78b36-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-123">TABLE_GUID</span></span>|<span data-ttu-id="78b36-124">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-124">Guid</span></span>|  
|<span data-ttu-id="78b36-125">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-125">DESCRIPTION</span></span>|<span data-ttu-id="78b36-126">String</span><span class="sxs-lookup"><span data-stu-id="78b36-126">String</span></span>|  
|<span data-ttu-id="78b36-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="78b36-127">TABLE_PROPID</span></span>|<span data-ttu-id="78b36-128">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-128">Int64</span></span>|  
|<span data-ttu-id="78b36-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="78b36-129">DATE_CREATED</span></span>|<span data-ttu-id="78b36-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-130">DateTime</span></span>|  
|<span data-ttu-id="78b36-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="78b36-131">DATE_MODIFIED</span></span>|<span data-ttu-id="78b36-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="78b36-133">Sloupce</span><span class="sxs-lookup"><span data-stu-id="78b36-133">Columns</span></span>  
  
|<span data-ttu-id="78b36-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-134">ColumnName</span></span>|<span data-ttu-id="78b36-135">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-136">TABLE_CATALOG</span></span>|<span data-ttu-id="78b36-137">String</span><span class="sxs-lookup"><span data-stu-id="78b36-137">String</span></span>|  
|<span data-ttu-id="78b36-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="78b36-139">String</span><span class="sxs-lookup"><span data-stu-id="78b36-139">String</span></span>|  
|<span data-ttu-id="78b36-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-140">TABLE_NAME</span></span>|<span data-ttu-id="78b36-141">String</span><span class="sxs-lookup"><span data-stu-id="78b36-141">String</span></span>|  
|<span data-ttu-id="78b36-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-142">COLUMN_NAME</span></span>|<span data-ttu-id="78b36-143">String</span><span class="sxs-lookup"><span data-stu-id="78b36-143">String</span></span>|  
|<span data-ttu-id="78b36-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-144">COLUMN_GUID</span></span>|<span data-ttu-id="78b36-145">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-145">Guid</span></span>|  
|<span data-ttu-id="78b36-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="78b36-146">COLUMN_PROPID</span></span>|<span data-ttu-id="78b36-147">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-147">Int64</span></span>|  
|<span data-ttu-id="78b36-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="78b36-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="78b36-149">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-149">Int64</span></span>|  
|<span data-ttu-id="78b36-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="78b36-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="78b36-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-151">Boolean</span></span>|  
|<span data-ttu-id="78b36-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="78b36-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="78b36-153">String</span><span class="sxs-lookup"><span data-stu-id="78b36-153">String</span></span>|  
|<span data-ttu-id="78b36-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="78b36-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="78b36-155">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-155">Int64</span></span>|  
|<span data-ttu-id="78b36-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="78b36-156">IS_NULLABLE</span></span>|<span data-ttu-id="78b36-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-157">Boolean</span></span>|  
|<span data-ttu-id="78b36-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="78b36-158">DATA_TYPE</span></span>|<span data-ttu-id="78b36-159">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-159">Int32</span></span>|  
|<span data-ttu-id="78b36-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-160">TYPE_GUID</span></span>|<span data-ttu-id="78b36-161">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-161">Guid</span></span>|  
|<span data-ttu-id="78b36-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="78b36-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="78b36-163">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-163">Int64</span></span>|  
|<span data-ttu-id="78b36-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="78b36-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="78b36-165">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-165">Int64</span></span>|  
|<span data-ttu-id="78b36-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="78b36-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="78b36-167">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-167">Int32</span></span>|  
|<span data-ttu-id="78b36-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="78b36-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="78b36-169">Int16</span><span class="sxs-lookup"><span data-stu-id="78b36-169">Int16</span></span>|  
|<span data-ttu-id="78b36-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="78b36-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="78b36-171">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-171">Int64</span></span>|  
|<span data-ttu-id="78b36-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="78b36-173">String</span><span class="sxs-lookup"><span data-stu-id="78b36-173">String</span></span>|  
|<span data-ttu-id="78b36-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="78b36-175">String</span><span class="sxs-lookup"><span data-stu-id="78b36-175">String</span></span>|  
|<span data-ttu-id="78b36-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="78b36-177">String</span><span class="sxs-lookup"><span data-stu-id="78b36-177">String</span></span>|  
|<span data-ttu-id="78b36-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="78b36-179">String</span><span class="sxs-lookup"><span data-stu-id="78b36-179">String</span></span>|  
|<span data-ttu-id="78b36-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="78b36-181">String</span><span class="sxs-lookup"><span data-stu-id="78b36-181">String</span></span>|  
|<span data-ttu-id="78b36-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-182">COLLATION_NAME</span></span>|<span data-ttu-id="78b36-183">String</span><span class="sxs-lookup"><span data-stu-id="78b36-183">String</span></span>|  
|<span data-ttu-id="78b36-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="78b36-185">String</span><span class="sxs-lookup"><span data-stu-id="78b36-185">String</span></span>|  
|<span data-ttu-id="78b36-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="78b36-187">String</span><span class="sxs-lookup"><span data-stu-id="78b36-187">String</span></span>|  
|<span data-ttu-id="78b36-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-188">DOMAIN_NAME</span></span>|<span data-ttu-id="78b36-189">String</span><span class="sxs-lookup"><span data-stu-id="78b36-189">String</span></span>|  
|<span data-ttu-id="78b36-190">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-190">DESCRIPTION</span></span>|<span data-ttu-id="78b36-191">String</span><span class="sxs-lookup"><span data-stu-id="78b36-191">String</span></span>|  
|<span data-ttu-id="78b36-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="78b36-192">COLUMN_LCID</span></span>|<span data-ttu-id="78b36-193">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-193">Int32</span></span>|  
|<span data-ttu-id="78b36-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="78b36-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="78b36-195">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-195">Int32</span></span>|  
|<span data-ttu-id="78b36-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="78b36-196">COLUMN_SORTID</span></span>|<span data-ttu-id="78b36-197">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-197">Int32</span></span>|  
|<span data-ttu-id="78b36-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="78b36-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="78b36-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="78b36-199">Byte[]</span></span>|  
|<span data-ttu-id="78b36-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="78b36-200">IS_COMPUTED</span></span>|<span data-ttu-id="78b36-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="78b36-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="78b36-202">Procedures</span></span>  
  
|<span data-ttu-id="78b36-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-203">ColumnName</span></span>|<span data-ttu-id="78b36-204">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="78b36-206">String</span><span class="sxs-lookup"><span data-stu-id="78b36-206">String</span></span>|  
|<span data-ttu-id="78b36-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="78b36-208">String</span><span class="sxs-lookup"><span data-stu-id="78b36-208">String</span></span>|  
|<span data-ttu-id="78b36-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="78b36-210">String</span><span class="sxs-lookup"><span data-stu-id="78b36-210">String</span></span>|  
|<span data-ttu-id="78b36-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="78b36-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="78b36-212">Int16</span><span class="sxs-lookup"><span data-stu-id="78b36-212">Int16</span></span>|  
|<span data-ttu-id="78b36-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="78b36-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="78b36-214">String</span><span class="sxs-lookup"><span data-stu-id="78b36-214">String</span></span>|  
|<span data-ttu-id="78b36-215">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-215">DESCRIPTION</span></span>|<span data-ttu-id="78b36-216">String</span><span class="sxs-lookup"><span data-stu-id="78b36-216">String</span></span>|  
|<span data-ttu-id="78b36-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="78b36-217">DATE_CREATED</span></span>|<span data-ttu-id="78b36-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-218">DateTime</span></span>|  
|<span data-ttu-id="78b36-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="78b36-219">DATE_MODIFIED</span></span>|<span data-ttu-id="78b36-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="78b36-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="78b36-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="78b36-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-222">ColumnName</span></span>|<span data-ttu-id="78b36-223">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="78b36-225">String</span><span class="sxs-lookup"><span data-stu-id="78b36-225">String</span></span>|  
|<span data-ttu-id="78b36-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="78b36-227">String</span><span class="sxs-lookup"><span data-stu-id="78b36-227">String</span></span>|  
|<span data-ttu-id="78b36-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="78b36-229">String</span><span class="sxs-lookup"><span data-stu-id="78b36-229">String</span></span>|  
|<span data-ttu-id="78b36-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-230">PARAMETER_NAME</span></span>|<span data-ttu-id="78b36-231">String</span><span class="sxs-lookup"><span data-stu-id="78b36-231">String</span></span>|  
|<span data-ttu-id="78b36-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="78b36-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="78b36-233">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-233">Int32</span></span>|  
|<span data-ttu-id="78b36-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="78b36-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="78b36-235">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-235">Int32</span></span>|  
|<span data-ttu-id="78b36-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="78b36-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="78b36-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-237">Boolean</span></span>|  
|<span data-ttu-id="78b36-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="78b36-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="78b36-239">String</span><span class="sxs-lookup"><span data-stu-id="78b36-239">String</span></span>|  
|<span data-ttu-id="78b36-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="78b36-240">IS_NULLABLE</span></span>|<span data-ttu-id="78b36-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-241">Boolean</span></span>|  
|<span data-ttu-id="78b36-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="78b36-242">DATA_TYPE</span></span>|<span data-ttu-id="78b36-243">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-243">Int32</span></span>|  
|<span data-ttu-id="78b36-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="78b36-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="78b36-245">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-245">Int64</span></span>|  
|<span data-ttu-id="78b36-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="78b36-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="78b36-247">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-247">Int64</span></span>|  
|<span data-ttu-id="78b36-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="78b36-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="78b36-249">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-249">Int32</span></span>|  
|<span data-ttu-id="78b36-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="78b36-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="78b36-251">Int16</span><span class="sxs-lookup"><span data-stu-id="78b36-251">Int16</span></span>|  
|<span data-ttu-id="78b36-252">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-252">DESCRIPTION</span></span>|<span data-ttu-id="78b36-253">String</span><span class="sxs-lookup"><span data-stu-id="78b36-253">String</span></span>|  
|<span data-ttu-id="78b36-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-254">TYPE_NAME</span></span>|<span data-ttu-id="78b36-255">String</span><span class="sxs-lookup"><span data-stu-id="78b36-255">String</span></span>|  
|<span data-ttu-id="78b36-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="78b36-257">String</span><span class="sxs-lookup"><span data-stu-id="78b36-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="78b36-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="78b36-258">Catalog</span></span>  
  
|<span data-ttu-id="78b36-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-259">ColumnName</span></span>|<span data-ttu-id="78b36-260">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-261">CATALOG_NAME</span></span>|<span data-ttu-id="78b36-262">String</span><span class="sxs-lookup"><span data-stu-id="78b36-262">String</span></span>|  
|<span data-ttu-id="78b36-263">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-263">DESCRIPTION</span></span>|<span data-ttu-id="78b36-264">String</span><span class="sxs-lookup"><span data-stu-id="78b36-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="78b36-265">Indexy</span><span class="sxs-lookup"><span data-stu-id="78b36-265">Indexes</span></span>  
  
|<span data-ttu-id="78b36-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-266">ColumnName</span></span>|<span data-ttu-id="78b36-267">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-268">TABLE_CATALOG</span></span>|<span data-ttu-id="78b36-269">String</span><span class="sxs-lookup"><span data-stu-id="78b36-269">String</span></span>|  
|<span data-ttu-id="78b36-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="78b36-271">String</span><span class="sxs-lookup"><span data-stu-id="78b36-271">String</span></span>|  
|<span data-ttu-id="78b36-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-272">TABLE_NAME</span></span>|<span data-ttu-id="78b36-273">String</span><span class="sxs-lookup"><span data-stu-id="78b36-273">String</span></span>|  
|<span data-ttu-id="78b36-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-274">INDEX_CATALOG</span></span>|<span data-ttu-id="78b36-275">String</span><span class="sxs-lookup"><span data-stu-id="78b36-275">String</span></span>|  
|<span data-ttu-id="78b36-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="78b36-277">String</span><span class="sxs-lookup"><span data-stu-id="78b36-277">String</span></span>|  
|<span data-ttu-id="78b36-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-278">INDEX_NAME</span></span>|<span data-ttu-id="78b36-279">String</span><span class="sxs-lookup"><span data-stu-id="78b36-279">String</span></span>|  
|<span data-ttu-id="78b36-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="78b36-280">PRIMARY_KEY</span></span>|<span data-ttu-id="78b36-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-281">Boolean</span></span>|  
|<span data-ttu-id="78b36-282">TABULKA</span><span class="sxs-lookup"><span data-stu-id="78b36-282">UNIQUE</span></span>|<span data-ttu-id="78b36-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-283">Boolean</span></span>|  
|<span data-ttu-id="78b36-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="78b36-284">CLUSTERED</span></span>|<span data-ttu-id="78b36-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-285">Boolean</span></span>|  
|<span data-ttu-id="78b36-286">TEXTOVÝ</span><span class="sxs-lookup"><span data-stu-id="78b36-286">TYPE</span></span>|<span data-ttu-id="78b36-287">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-287">Int32</span></span>|  
|<span data-ttu-id="78b36-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="78b36-288">FILL_FACTOR</span></span>|<span data-ttu-id="78b36-289">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-289">Int32</span></span>|  
|<span data-ttu-id="78b36-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="78b36-290">INITIAL_SIZE</span></span>|<span data-ttu-id="78b36-291">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-291">Int32</span></span>|  
|<span data-ttu-id="78b36-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="78b36-292">NULLS</span></span>|<span data-ttu-id="78b36-293">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-293">Int32</span></span>|  
|<span data-ttu-id="78b36-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="78b36-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="78b36-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-295">Boolean</span></span>|  
|<span data-ttu-id="78b36-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="78b36-296">AUTO_UPDATE</span></span>|<span data-ttu-id="78b36-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-297">Boolean</span></span>|  
|<span data-ttu-id="78b36-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="78b36-298">NULL_COLLATION</span></span>|<span data-ttu-id="78b36-299">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-299">Int32</span></span>|  
|<span data-ttu-id="78b36-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="78b36-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="78b36-301">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-301">Int64</span></span>|  
|<span data-ttu-id="78b36-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-302">COLUMN_NAME</span></span>|<span data-ttu-id="78b36-303">String</span><span class="sxs-lookup"><span data-stu-id="78b36-303">String</span></span>|  
|<span data-ttu-id="78b36-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-304">COLUMN_GUID</span></span>|<span data-ttu-id="78b36-305">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-305">Guid</span></span>|  
|<span data-ttu-id="78b36-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="78b36-306">COLUMN_PROPID</span></span>|<span data-ttu-id="78b36-307">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-307">Int64</span></span>|  
|<span data-ttu-id="78b36-308">VELKÉ</span><span class="sxs-lookup"><span data-stu-id="78b36-308">COLLATION</span></span>|<span data-ttu-id="78b36-309">Int16</span><span class="sxs-lookup"><span data-stu-id="78b36-309">Int16</span></span>|  
|<span data-ttu-id="78b36-310">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="78b36-310">CARDINALITY</span></span>|<span data-ttu-id="78b36-311">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="78b36-311">Decimal</span></span>|  
|<span data-ttu-id="78b36-312">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="78b36-312">PAGES</span></span>|<span data-ttu-id="78b36-313">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-313">Int32</span></span>|  
|<span data-ttu-id="78b36-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="78b36-314">FILTER_CONDITION</span></span>|<span data-ttu-id="78b36-315">String</span><span class="sxs-lookup"><span data-stu-id="78b36-315">String</span></span>|  
|<span data-ttu-id="78b36-316">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="78b36-316">INTEGRATED</span></span>|<span data-ttu-id="78b36-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="78b36-318">Zprostředkovatel Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="78b36-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="78b36-319">Microsoft Oracle OLE DB Driver podporuje kromě běžných kolekcí schémat následující konkrétní kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="78b36-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="78b36-320">Tabulky</span><span class="sxs-lookup"><span data-stu-id="78b36-320">Tables</span></span>  
  
- <span data-ttu-id="78b36-321">Sloupce</span><span class="sxs-lookup"><span data-stu-id="78b36-321">Columns</span></span>  
  
- <span data-ttu-id="78b36-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="78b36-322">Procedures</span></span>  
  
- <span data-ttu-id="78b36-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="78b36-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="78b36-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="78b36-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="78b36-325">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="78b36-325">Views</span></span>  
  
- <span data-ttu-id="78b36-326">Indexy</span><span class="sxs-lookup"><span data-stu-id="78b36-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="78b36-327">Tabulky</span><span class="sxs-lookup"><span data-stu-id="78b36-327">Tables</span></span>  
  
|<span data-ttu-id="78b36-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-328">ColumnName</span></span>|<span data-ttu-id="78b36-329">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-330">TABLE_CATALOG</span></span>|<span data-ttu-id="78b36-331">String</span><span class="sxs-lookup"><span data-stu-id="78b36-331">String</span></span>|  
|<span data-ttu-id="78b36-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="78b36-333">String</span><span class="sxs-lookup"><span data-stu-id="78b36-333">String</span></span>|  
|<span data-ttu-id="78b36-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-334">TABLE_NAME</span></span>|<span data-ttu-id="78b36-335">String</span><span class="sxs-lookup"><span data-stu-id="78b36-335">String</span></span>|  
|<span data-ttu-id="78b36-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="78b36-336">TABLE_TYPE</span></span>|<span data-ttu-id="78b36-337">String</span><span class="sxs-lookup"><span data-stu-id="78b36-337">String</span></span>|  
|<span data-ttu-id="78b36-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-338">TABLE_GUID</span></span>|<span data-ttu-id="78b36-339">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-339">Guid</span></span>|  
|<span data-ttu-id="78b36-340">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-340">DESCRIPTION</span></span>|<span data-ttu-id="78b36-341">String</span><span class="sxs-lookup"><span data-stu-id="78b36-341">String</span></span>|  
|<span data-ttu-id="78b36-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="78b36-342">TABLE_PROPID</span></span>|<span data-ttu-id="78b36-343">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-343">Int64</span></span>|  
|<span data-ttu-id="78b36-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="78b36-344">DATE_CREATED</span></span>|<span data-ttu-id="78b36-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-345">DateTime</span></span>|  
|<span data-ttu-id="78b36-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="78b36-346">DATE_MODIFIED</span></span>|<span data-ttu-id="78b36-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="78b36-348">Sloupce</span><span class="sxs-lookup"><span data-stu-id="78b36-348">Columns</span></span>  
  
|<span data-ttu-id="78b36-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-349">ColumnName</span></span>|<span data-ttu-id="78b36-350">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-351">TABLE_CATALOG</span></span>|<span data-ttu-id="78b36-352">String</span><span class="sxs-lookup"><span data-stu-id="78b36-352">String</span></span>|  
|<span data-ttu-id="78b36-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="78b36-354">String</span><span class="sxs-lookup"><span data-stu-id="78b36-354">String</span></span>|  
|<span data-ttu-id="78b36-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-355">TABLE_NAME</span></span>|<span data-ttu-id="78b36-356">String</span><span class="sxs-lookup"><span data-stu-id="78b36-356">String</span></span>|  
|<span data-ttu-id="78b36-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-357">COLUMN_NAME</span></span>|<span data-ttu-id="78b36-358">String</span><span class="sxs-lookup"><span data-stu-id="78b36-358">String</span></span>|  
|<span data-ttu-id="78b36-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-359">COLUMN_GUID</span></span>|<span data-ttu-id="78b36-360">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-360">Guid</span></span>|  
|<span data-ttu-id="78b36-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="78b36-361">COLUMN_PROPID</span></span>|<span data-ttu-id="78b36-362">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-362">Int64</span></span>|  
|<span data-ttu-id="78b36-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="78b36-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="78b36-364">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-364">Int64</span></span>|  
|<span data-ttu-id="78b36-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="78b36-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="78b36-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-366">Boolean</span></span>|  
|<span data-ttu-id="78b36-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="78b36-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="78b36-368">String</span><span class="sxs-lookup"><span data-stu-id="78b36-368">String</span></span>|  
|<span data-ttu-id="78b36-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="78b36-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="78b36-370">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-370">Int64</span></span>|  
|<span data-ttu-id="78b36-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="78b36-371">IS_NULLABLE</span></span>|<span data-ttu-id="78b36-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-372">Boolean</span></span>|  
|<span data-ttu-id="78b36-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="78b36-373">DATA_TYPE</span></span>|<span data-ttu-id="78b36-374">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-374">Int32</span></span>|  
|<span data-ttu-id="78b36-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-375">TYPE_GUID</span></span>|<span data-ttu-id="78b36-376">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-376">Guid</span></span>|  
|<span data-ttu-id="78b36-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="78b36-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="78b36-378">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-378">Int64</span></span>|  
|<span data-ttu-id="78b36-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="78b36-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="78b36-380">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-380">Int64</span></span>|  
|<span data-ttu-id="78b36-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="78b36-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="78b36-382">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-382">Int32</span></span>|  
|<span data-ttu-id="78b36-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="78b36-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="78b36-384">Int16</span><span class="sxs-lookup"><span data-stu-id="78b36-384">Int16</span></span>|  
|<span data-ttu-id="78b36-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="78b36-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="78b36-386">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-386">Int64</span></span>|  
|<span data-ttu-id="78b36-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="78b36-388">String</span><span class="sxs-lookup"><span data-stu-id="78b36-388">String</span></span>|  
|<span data-ttu-id="78b36-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="78b36-390">String</span><span class="sxs-lookup"><span data-stu-id="78b36-390">String</span></span>|  
|<span data-ttu-id="78b36-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="78b36-392">String</span><span class="sxs-lookup"><span data-stu-id="78b36-392">String</span></span>|  
|<span data-ttu-id="78b36-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="78b36-394">String</span><span class="sxs-lookup"><span data-stu-id="78b36-394">String</span></span>|  
|<span data-ttu-id="78b36-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="78b36-396">String</span><span class="sxs-lookup"><span data-stu-id="78b36-396">String</span></span>|  
|<span data-ttu-id="78b36-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-397">COLLATION_NAME</span></span>|<span data-ttu-id="78b36-398">String</span><span class="sxs-lookup"><span data-stu-id="78b36-398">String</span></span>|  
|<span data-ttu-id="78b36-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="78b36-400">String</span><span class="sxs-lookup"><span data-stu-id="78b36-400">String</span></span>|  
|<span data-ttu-id="78b36-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="78b36-402">String</span><span class="sxs-lookup"><span data-stu-id="78b36-402">String</span></span>|  
|<span data-ttu-id="78b36-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-403">DOMAIN_NAME</span></span>|<span data-ttu-id="78b36-404">String</span><span class="sxs-lookup"><span data-stu-id="78b36-404">String</span></span>|  
|<span data-ttu-id="78b36-405">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-405">DESCRIPTION</span></span>|<span data-ttu-id="78b36-406">String</span><span class="sxs-lookup"><span data-stu-id="78b36-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="78b36-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="78b36-407">Procedures</span></span>  
  
|<span data-ttu-id="78b36-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-408">ColumnName</span></span>|<span data-ttu-id="78b36-409">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="78b36-411">String</span><span class="sxs-lookup"><span data-stu-id="78b36-411">String</span></span>|  
|<span data-ttu-id="78b36-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="78b36-413">String</span><span class="sxs-lookup"><span data-stu-id="78b36-413">String</span></span>|  
|<span data-ttu-id="78b36-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="78b36-415">String</span><span class="sxs-lookup"><span data-stu-id="78b36-415">String</span></span>|  
|<span data-ttu-id="78b36-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="78b36-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="78b36-417">Int16</span><span class="sxs-lookup"><span data-stu-id="78b36-417">Int16</span></span>|  
|<span data-ttu-id="78b36-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="78b36-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="78b36-419">String</span><span class="sxs-lookup"><span data-stu-id="78b36-419">String</span></span>|  
|<span data-ttu-id="78b36-420">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-420">DESCRIPTION</span></span>|<span data-ttu-id="78b36-421">String</span><span class="sxs-lookup"><span data-stu-id="78b36-421">String</span></span>|  
|<span data-ttu-id="78b36-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="78b36-422">DATE_CREATED</span></span>|<span data-ttu-id="78b36-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-423">DateTime</span></span>|  
|<span data-ttu-id="78b36-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="78b36-424">DATE_MODIFIED</span></span>|<span data-ttu-id="78b36-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="78b36-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="78b36-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="78b36-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-427">ColumnName</span></span>|<span data-ttu-id="78b36-428">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="78b36-430">String</span><span class="sxs-lookup"><span data-stu-id="78b36-430">String</span></span>|  
|<span data-ttu-id="78b36-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="78b36-432">String</span><span class="sxs-lookup"><span data-stu-id="78b36-432">String</span></span>|  
|<span data-ttu-id="78b36-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="78b36-434">String</span><span class="sxs-lookup"><span data-stu-id="78b36-434">String</span></span>|  
|<span data-ttu-id="78b36-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-435">COLUMN_NAME</span></span>|<span data-ttu-id="78b36-436">String</span><span class="sxs-lookup"><span data-stu-id="78b36-436">String</span></span>|  
|<span data-ttu-id="78b36-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-437">COLUMN_GUID</span></span>|<span data-ttu-id="78b36-438">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-438">Guid</span></span>|  
|<span data-ttu-id="78b36-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="78b36-439">COLUMN_PROPID</span></span>|<span data-ttu-id="78b36-440">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-440">Int64</span></span>|  
|<span data-ttu-id="78b36-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="78b36-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="78b36-442">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-442">Int64</span></span>|  
|<span data-ttu-id="78b36-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="78b36-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="78b36-444">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-444">Int64</span></span>|  
|<span data-ttu-id="78b36-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="78b36-445">IS_NULLABLE</span></span>|<span data-ttu-id="78b36-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-446">Boolean</span></span>|  
|<span data-ttu-id="78b36-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="78b36-447">DATA_TYPE</span></span>|<span data-ttu-id="78b36-448">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-448">Int32</span></span>|  
|<span data-ttu-id="78b36-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-449">TYPE_GUID</span></span>|<span data-ttu-id="78b36-450">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-450">Guid</span></span>|  
|<span data-ttu-id="78b36-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="78b36-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="78b36-452">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-452">Int64</span></span>|  
|<span data-ttu-id="78b36-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="78b36-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="78b36-454">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-454">Int64</span></span>|  
|<span data-ttu-id="78b36-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="78b36-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="78b36-456">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-456">Int32</span></span>|  
|<span data-ttu-id="78b36-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="78b36-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="78b36-458">Int16</span><span class="sxs-lookup"><span data-stu-id="78b36-458">Int16</span></span>|  
|<span data-ttu-id="78b36-459">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-459">DESCRIPTION</span></span>|<span data-ttu-id="78b36-460">String</span><span class="sxs-lookup"><span data-stu-id="78b36-460">String</span></span>|  
|<span data-ttu-id="78b36-461">METODY</span><span class="sxs-lookup"><span data-stu-id="78b36-461">OVERLOAD</span></span>|<span data-ttu-id="78b36-462">Int16</span><span class="sxs-lookup"><span data-stu-id="78b36-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="78b36-463">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="78b36-463">Views</span></span>  
  
|<span data-ttu-id="78b36-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-464">ColumnName</span></span>|<span data-ttu-id="78b36-465">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-466">TABLE_CATALOG</span></span>|<span data-ttu-id="78b36-467">String</span><span class="sxs-lookup"><span data-stu-id="78b36-467">String</span></span>|  
|<span data-ttu-id="78b36-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="78b36-469">String</span><span class="sxs-lookup"><span data-stu-id="78b36-469">String</span></span>|  
|<span data-ttu-id="78b36-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-470">TABLE_NAME</span></span>|<span data-ttu-id="78b36-471">String</span><span class="sxs-lookup"><span data-stu-id="78b36-471">String</span></span>|  
|<span data-ttu-id="78b36-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="78b36-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="78b36-473">String</span><span class="sxs-lookup"><span data-stu-id="78b36-473">String</span></span>|  
|<span data-ttu-id="78b36-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="78b36-474">CHECK_OPTION</span></span>|<span data-ttu-id="78b36-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-475">Boolean</span></span>|  
|<span data-ttu-id="78b36-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="78b36-476">IS_UPDATABLE</span></span>|<span data-ttu-id="78b36-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-477">Boolean</span></span>|  
|<span data-ttu-id="78b36-478">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-478">DESCRIPTION</span></span>|<span data-ttu-id="78b36-479">String</span><span class="sxs-lookup"><span data-stu-id="78b36-479">String</span></span>|  
|<span data-ttu-id="78b36-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="78b36-480">DATE_CREATED</span></span>|<span data-ttu-id="78b36-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-481">DateTime</span></span>|  
|<span data-ttu-id="78b36-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="78b36-482">DATE_MODIFIED</span></span>|<span data-ttu-id="78b36-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="78b36-484">Indexy</span><span class="sxs-lookup"><span data-stu-id="78b36-484">Indexes</span></span>  
  
|<span data-ttu-id="78b36-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-485">ColumnName</span></span>|<span data-ttu-id="78b36-486">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-487">TABLE_CATALOG</span></span>|<span data-ttu-id="78b36-488">String</span><span class="sxs-lookup"><span data-stu-id="78b36-488">String</span></span>|  
|<span data-ttu-id="78b36-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="78b36-490">String</span><span class="sxs-lookup"><span data-stu-id="78b36-490">String</span></span>|  
|<span data-ttu-id="78b36-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-491">TABLE_NAME</span></span>|<span data-ttu-id="78b36-492">String</span><span class="sxs-lookup"><span data-stu-id="78b36-492">String</span></span>|  
|<span data-ttu-id="78b36-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-493">INDEX_CATALOG</span></span>|<span data-ttu-id="78b36-494">String</span><span class="sxs-lookup"><span data-stu-id="78b36-494">String</span></span>|  
|<span data-ttu-id="78b36-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="78b36-496">String</span><span class="sxs-lookup"><span data-stu-id="78b36-496">String</span></span>|  
|<span data-ttu-id="78b36-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-497">INDEX_NAME</span></span>|<span data-ttu-id="78b36-498">String</span><span class="sxs-lookup"><span data-stu-id="78b36-498">String</span></span>|  
|<span data-ttu-id="78b36-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="78b36-499">PRIMARY_KEY</span></span>|<span data-ttu-id="78b36-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-500">Boolean</span></span>|  
|<span data-ttu-id="78b36-501">TABULKA</span><span class="sxs-lookup"><span data-stu-id="78b36-501">UNIQUE</span></span>|<span data-ttu-id="78b36-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-502">Boolean</span></span>|  
|<span data-ttu-id="78b36-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="78b36-503">CLUSTERED</span></span>|<span data-ttu-id="78b36-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-504">Boolean</span></span>|  
|<span data-ttu-id="78b36-505">TEXTOVÝ</span><span class="sxs-lookup"><span data-stu-id="78b36-505">TYPE</span></span>|<span data-ttu-id="78b36-506">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-506">Int32</span></span>|  
|<span data-ttu-id="78b36-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="78b36-507">FILL_FACTOR</span></span>|<span data-ttu-id="78b36-508">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-508">Int32</span></span>|  
|<span data-ttu-id="78b36-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="78b36-509">INITIAL_SIZE</span></span>|<span data-ttu-id="78b36-510">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-510">Int32</span></span>|  
|<span data-ttu-id="78b36-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="78b36-511">NULLS</span></span>|<span data-ttu-id="78b36-512">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-512">Int32</span></span>|  
|<span data-ttu-id="78b36-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="78b36-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="78b36-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-514">Boolean</span></span>|  
|<span data-ttu-id="78b36-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="78b36-515">AUTO_UPDATE</span></span>|<span data-ttu-id="78b36-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-516">Boolean</span></span>|  
|<span data-ttu-id="78b36-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="78b36-517">NULL_COLLATION</span></span>|<span data-ttu-id="78b36-518">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-518">Int32</span></span>|  
|<span data-ttu-id="78b36-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="78b36-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="78b36-520">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-520">Int64</span></span>|  
|<span data-ttu-id="78b36-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-521">COLUMN_NAME</span></span>|<span data-ttu-id="78b36-522">String</span><span class="sxs-lookup"><span data-stu-id="78b36-522">String</span></span>|  
|<span data-ttu-id="78b36-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-523">COLUMN_GUID</span></span>|<span data-ttu-id="78b36-524">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-524">Guid</span></span>|  
|<span data-ttu-id="78b36-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="78b36-525">COLUMN_PROPID</span></span>|<span data-ttu-id="78b36-526">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-526">Int64</span></span>|  
|<span data-ttu-id="78b36-527">VELKÉ</span><span class="sxs-lookup"><span data-stu-id="78b36-527">COLLATION</span></span>|<span data-ttu-id="78b36-528">Int16</span><span class="sxs-lookup"><span data-stu-id="78b36-528">Int16</span></span>|  
|<span data-ttu-id="78b36-529">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="78b36-529">CARDINALITY</span></span>|<span data-ttu-id="78b36-530">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="78b36-530">Decimal</span></span>|  
|<span data-ttu-id="78b36-531">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="78b36-531">PAGES</span></span>|<span data-ttu-id="78b36-532">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-532">Int32</span></span>|  
|<span data-ttu-id="78b36-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="78b36-533">FILTER_CONDITION</span></span>|<span data-ttu-id="78b36-534">String</span><span class="sxs-lookup"><span data-stu-id="78b36-534">String</span></span>|  
|<span data-ttu-id="78b36-535">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="78b36-535">INTEGRATED</span></span>|<span data-ttu-id="78b36-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="78b36-537">Zprostředkovatel Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="78b36-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="78b36-538">Ovladač Microsoft Jet OLE DB podporuje kromě běžných kolekcí schémat následující konkrétní kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="78b36-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="78b36-539">Tabulky</span><span class="sxs-lookup"><span data-stu-id="78b36-539">Tables</span></span>  
  
- <span data-ttu-id="78b36-540">Sloupce</span><span class="sxs-lookup"><span data-stu-id="78b36-540">Columns</span></span>  
  
- <span data-ttu-id="78b36-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="78b36-541">Procedures</span></span>  
  
- <span data-ttu-id="78b36-542">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="78b36-542">Views</span></span>  
  
- <span data-ttu-id="78b36-543">Indexy</span><span class="sxs-lookup"><span data-stu-id="78b36-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="78b36-544">Tabulky</span><span class="sxs-lookup"><span data-stu-id="78b36-544">Tables</span></span>  
  
|<span data-ttu-id="78b36-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-545">ColumnName</span></span>|<span data-ttu-id="78b36-546">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-547">TABLE_CATALOG</span></span>|<span data-ttu-id="78b36-548">String</span><span class="sxs-lookup"><span data-stu-id="78b36-548">String</span></span>|  
|<span data-ttu-id="78b36-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="78b36-550">String</span><span class="sxs-lookup"><span data-stu-id="78b36-550">String</span></span>|  
|<span data-ttu-id="78b36-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-551">TABLE_NAME</span></span>|<span data-ttu-id="78b36-552">String</span><span class="sxs-lookup"><span data-stu-id="78b36-552">String</span></span>|  
|<span data-ttu-id="78b36-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="78b36-553">TABLE_TYPE</span></span>|<span data-ttu-id="78b36-554">String</span><span class="sxs-lookup"><span data-stu-id="78b36-554">String</span></span>|  
|<span data-ttu-id="78b36-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-555">TABLE_GUID</span></span>|<span data-ttu-id="78b36-556">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-556">Guid</span></span>|  
|<span data-ttu-id="78b36-557">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-557">DESCRIPTION</span></span>|<span data-ttu-id="78b36-558">String</span><span class="sxs-lookup"><span data-stu-id="78b36-558">String</span></span>|  
|<span data-ttu-id="78b36-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="78b36-559">TABLE_PROPID</span></span>|<span data-ttu-id="78b36-560">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-560">Int64</span></span>|  
|<span data-ttu-id="78b36-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="78b36-561">DATE_CREATED</span></span>|<span data-ttu-id="78b36-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-562">DateTime</span></span>|  
|<span data-ttu-id="78b36-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="78b36-563">DATE_MODIFIED</span></span>|<span data-ttu-id="78b36-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="78b36-565">Sloupce</span><span class="sxs-lookup"><span data-stu-id="78b36-565">Columns</span></span>  
  
|<span data-ttu-id="78b36-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-566">ColumnName</span></span>|<span data-ttu-id="78b36-567">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-568">TABLE_CATALOG</span></span>|<span data-ttu-id="78b36-569">String</span><span class="sxs-lookup"><span data-stu-id="78b36-569">String</span></span>|  
|<span data-ttu-id="78b36-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="78b36-571">String</span><span class="sxs-lookup"><span data-stu-id="78b36-571">String</span></span>|  
|<span data-ttu-id="78b36-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-572">TABLE_NAME</span></span>|<span data-ttu-id="78b36-573">String</span><span class="sxs-lookup"><span data-stu-id="78b36-573">String</span></span>|  
|<span data-ttu-id="78b36-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-574">COLUMN_NAME</span></span>|<span data-ttu-id="78b36-575">String</span><span class="sxs-lookup"><span data-stu-id="78b36-575">String</span></span>|  
|<span data-ttu-id="78b36-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-576">COLUMN_GUID</span></span>|<span data-ttu-id="78b36-577">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-577">Guid</span></span>|  
|<span data-ttu-id="78b36-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="78b36-578">COLUMN_PROPID</span></span>|<span data-ttu-id="78b36-579">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-579">Int64</span></span>|  
|<span data-ttu-id="78b36-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="78b36-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="78b36-581">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-581">Int64</span></span>|  
|<span data-ttu-id="78b36-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="78b36-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="78b36-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-583">Boolean</span></span>|  
|<span data-ttu-id="78b36-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="78b36-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="78b36-585">String</span><span class="sxs-lookup"><span data-stu-id="78b36-585">String</span></span>|  
|<span data-ttu-id="78b36-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="78b36-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="78b36-587">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-587">Int64</span></span>|  
|<span data-ttu-id="78b36-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="78b36-588">IS_NULLABLE</span></span>|<span data-ttu-id="78b36-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-589">Boolean</span></span>|  
|<span data-ttu-id="78b36-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="78b36-590">DATA_TYPE</span></span>|<span data-ttu-id="78b36-591">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-591">Int32</span></span>|  
|<span data-ttu-id="78b36-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-592">TYPE_GUID</span></span>|<span data-ttu-id="78b36-593">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-593">Guid</span></span>|  
|<span data-ttu-id="78b36-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="78b36-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="78b36-595">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-595">Int64</span></span>|  
|<span data-ttu-id="78b36-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="78b36-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="78b36-597">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-597">Int64</span></span>|  
|<span data-ttu-id="78b36-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="78b36-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="78b36-599">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-599">Int32</span></span>|  
|<span data-ttu-id="78b36-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="78b36-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="78b36-601">Int16</span><span class="sxs-lookup"><span data-stu-id="78b36-601">Int16</span></span>|  
|<span data-ttu-id="78b36-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="78b36-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="78b36-603">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-603">Int64</span></span>|  
|<span data-ttu-id="78b36-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="78b36-605">String</span><span class="sxs-lookup"><span data-stu-id="78b36-605">String</span></span>|  
|<span data-ttu-id="78b36-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="78b36-607">String</span><span class="sxs-lookup"><span data-stu-id="78b36-607">String</span></span>|  
|<span data-ttu-id="78b36-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="78b36-609">String</span><span class="sxs-lookup"><span data-stu-id="78b36-609">String</span></span>|  
|<span data-ttu-id="78b36-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="78b36-611">String</span><span class="sxs-lookup"><span data-stu-id="78b36-611">String</span></span>|  
|<span data-ttu-id="78b36-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="78b36-613">String</span><span class="sxs-lookup"><span data-stu-id="78b36-613">String</span></span>|  
|<span data-ttu-id="78b36-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-614">COLLATION_NAME</span></span>|<span data-ttu-id="78b36-615">String</span><span class="sxs-lookup"><span data-stu-id="78b36-615">String</span></span>|  
|<span data-ttu-id="78b36-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="78b36-617">String</span><span class="sxs-lookup"><span data-stu-id="78b36-617">String</span></span>|  
|<span data-ttu-id="78b36-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="78b36-619">String</span><span class="sxs-lookup"><span data-stu-id="78b36-619">String</span></span>|  
|<span data-ttu-id="78b36-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-620">DOMAIN_NAME</span></span>|<span data-ttu-id="78b36-621">String</span><span class="sxs-lookup"><span data-stu-id="78b36-621">String</span></span>|  
|<span data-ttu-id="78b36-622">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-622">DESCRIPTION</span></span>|<span data-ttu-id="78b36-623">String</span><span class="sxs-lookup"><span data-stu-id="78b36-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="78b36-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="78b36-624">Procedures</span></span>  
  
|<span data-ttu-id="78b36-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-625">ColumnName</span></span>|<span data-ttu-id="78b36-626">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="78b36-628">String</span><span class="sxs-lookup"><span data-stu-id="78b36-628">String</span></span>|  
|<span data-ttu-id="78b36-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="78b36-630">String</span><span class="sxs-lookup"><span data-stu-id="78b36-630">String</span></span>|  
|<span data-ttu-id="78b36-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="78b36-632">String</span><span class="sxs-lookup"><span data-stu-id="78b36-632">String</span></span>|  
|<span data-ttu-id="78b36-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="78b36-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="78b36-634">Int16</span><span class="sxs-lookup"><span data-stu-id="78b36-634">Int16</span></span>|  
|<span data-ttu-id="78b36-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="78b36-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="78b36-636">String</span><span class="sxs-lookup"><span data-stu-id="78b36-636">String</span></span>|  
|<span data-ttu-id="78b36-637">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-637">DESCRIPTION</span></span>|<span data-ttu-id="78b36-638">String</span><span class="sxs-lookup"><span data-stu-id="78b36-638">String</span></span>|  
|<span data-ttu-id="78b36-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="78b36-639">DATE_CREATED</span></span>|<span data-ttu-id="78b36-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-640">DateTime</span></span>|  
|<span data-ttu-id="78b36-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="78b36-641">DATE_MODIFIED</span></span>|<span data-ttu-id="78b36-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="78b36-643">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="78b36-643">Views</span></span>  
  
|<span data-ttu-id="78b36-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-644">ColumnName</span></span>|<span data-ttu-id="78b36-645">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-646">TABLE_CATALOG</span></span>|<span data-ttu-id="78b36-647">String</span><span class="sxs-lookup"><span data-stu-id="78b36-647">String</span></span>|  
|<span data-ttu-id="78b36-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="78b36-649">String</span><span class="sxs-lookup"><span data-stu-id="78b36-649">String</span></span>|  
|<span data-ttu-id="78b36-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-650">TABLE_NAME</span></span>|<span data-ttu-id="78b36-651">String</span><span class="sxs-lookup"><span data-stu-id="78b36-651">String</span></span>|  
|<span data-ttu-id="78b36-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="78b36-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="78b36-653">String</span><span class="sxs-lookup"><span data-stu-id="78b36-653">String</span></span>|  
|<span data-ttu-id="78b36-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="78b36-654">CHECK_OPTION</span></span>|<span data-ttu-id="78b36-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-655">Boolean</span></span>|  
|<span data-ttu-id="78b36-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="78b36-656">IS_UPDATABLE</span></span>|<span data-ttu-id="78b36-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-657">Boolean</span></span>|  
|<span data-ttu-id="78b36-658">NÁZEV</span><span class="sxs-lookup"><span data-stu-id="78b36-658">DESCRIPTION</span></span>|<span data-ttu-id="78b36-659">String</span><span class="sxs-lookup"><span data-stu-id="78b36-659">String</span></span>|  
|<span data-ttu-id="78b36-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="78b36-660">DATE_CREATED</span></span>|<span data-ttu-id="78b36-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-661">DateTime</span></span>|  
|<span data-ttu-id="78b36-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="78b36-662">DATE_MODIFIED</span></span>|<span data-ttu-id="78b36-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="78b36-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="78b36-664">Indexy</span><span class="sxs-lookup"><span data-stu-id="78b36-664">Indexes</span></span>  
  
|<span data-ttu-id="78b36-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="78b36-665">ColumnName</span></span>|<span data-ttu-id="78b36-666">DataType</span><span class="sxs-lookup"><span data-stu-id="78b36-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="78b36-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-667">TABLE_CATALOG</span></span>|<span data-ttu-id="78b36-668">String</span><span class="sxs-lookup"><span data-stu-id="78b36-668">String</span></span>|  
|<span data-ttu-id="78b36-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="78b36-670">String</span><span class="sxs-lookup"><span data-stu-id="78b36-670">String</span></span>|  
|<span data-ttu-id="78b36-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-671">TABLE_NAME</span></span>|<span data-ttu-id="78b36-672">String</span><span class="sxs-lookup"><span data-stu-id="78b36-672">String</span></span>|  
|<span data-ttu-id="78b36-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78b36-673">INDEX_CATALOG</span></span>|<span data-ttu-id="78b36-674">String</span><span class="sxs-lookup"><span data-stu-id="78b36-674">String</span></span>|  
|<span data-ttu-id="78b36-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78b36-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="78b36-676">String</span><span class="sxs-lookup"><span data-stu-id="78b36-676">String</span></span>|  
|<span data-ttu-id="78b36-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-677">INDEX_NAME</span></span>|<span data-ttu-id="78b36-678">String</span><span class="sxs-lookup"><span data-stu-id="78b36-678">String</span></span>|  
|<span data-ttu-id="78b36-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="78b36-679">PRIMARY_KEY</span></span>|<span data-ttu-id="78b36-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-680">Boolean</span></span>|  
|<span data-ttu-id="78b36-681">TABULKA</span><span class="sxs-lookup"><span data-stu-id="78b36-681">UNIQUE</span></span>|<span data-ttu-id="78b36-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-682">Boolean</span></span>|  
|<span data-ttu-id="78b36-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="78b36-683">CLUSTERED</span></span>|<span data-ttu-id="78b36-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-684">Boolean</span></span>|  
|<span data-ttu-id="78b36-685">TEXTOVÝ</span><span class="sxs-lookup"><span data-stu-id="78b36-685">TYPE</span></span>|<span data-ttu-id="78b36-686">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-686">Int32</span></span>|  
|<span data-ttu-id="78b36-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="78b36-687">FILL_FACTOR</span></span>|<span data-ttu-id="78b36-688">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-688">Int32</span></span>|  
|<span data-ttu-id="78b36-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="78b36-689">INITIAL_SIZE</span></span>|<span data-ttu-id="78b36-690">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-690">Int32</span></span>|  
|<span data-ttu-id="78b36-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="78b36-691">NULLS</span></span>|<span data-ttu-id="78b36-692">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-692">Int32</span></span>|  
|<span data-ttu-id="78b36-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="78b36-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="78b36-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-694">Boolean</span></span>|  
|<span data-ttu-id="78b36-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="78b36-695">AUTO_UPDATE</span></span>|<span data-ttu-id="78b36-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-696">Boolean</span></span>|  
|<span data-ttu-id="78b36-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="78b36-697">NULL_COLLATION</span></span>|<span data-ttu-id="78b36-698">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-698">Int32</span></span>|  
|<span data-ttu-id="78b36-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="78b36-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="78b36-700">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-700">Int64</span></span>|  
|<span data-ttu-id="78b36-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="78b36-701">COLUMN_NAME</span></span>|<span data-ttu-id="78b36-702">String</span><span class="sxs-lookup"><span data-stu-id="78b36-702">String</span></span>|  
|<span data-ttu-id="78b36-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="78b36-703">COLUMN_GUID</span></span>|<span data-ttu-id="78b36-704">Guid</span><span class="sxs-lookup"><span data-stu-id="78b36-704">Guid</span></span>|  
|<span data-ttu-id="78b36-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="78b36-705">COLUMN_PROPID</span></span>|<span data-ttu-id="78b36-706">Int64</span><span class="sxs-lookup"><span data-stu-id="78b36-706">Int64</span></span>|  
|<span data-ttu-id="78b36-707">VELKÉ</span><span class="sxs-lookup"><span data-stu-id="78b36-707">COLLATION</span></span>|<span data-ttu-id="78b36-708">Int16</span><span class="sxs-lookup"><span data-stu-id="78b36-708">Int16</span></span>|  
|<span data-ttu-id="78b36-709">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="78b36-709">CARDINALITY</span></span>|<span data-ttu-id="78b36-710">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="78b36-710">Decimal</span></span>|  
|<span data-ttu-id="78b36-711">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="78b36-711">PAGES</span></span>|<span data-ttu-id="78b36-712">Int32</span><span class="sxs-lookup"><span data-stu-id="78b36-712">Int32</span></span>|  
|<span data-ttu-id="78b36-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="78b36-713">FILTER_CONDITION</span></span>|<span data-ttu-id="78b36-714">String</span><span class="sxs-lookup"><span data-stu-id="78b36-714">String</span></span>|  
|<span data-ttu-id="78b36-715">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="78b36-715">INTEGRATED</span></span>|<span data-ttu-id="78b36-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="78b36-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78b36-717">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78b36-717">See also</span></span>

- [<span data-ttu-id="78b36-718">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="78b36-718">ADO.NET Overview</span></span>](ado-net-overview.md)
